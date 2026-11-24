---
description: >-
  Connect Airy Lite 24-channel Ethernet LiDAR with its 3.3 V PPS limit, decode
  calibrated cloud/IMU data using RSAIRYLITE_ETH, and diagnose periodic scan
  gaps.
---

# RoboSense Airy Lite LiDAR Engineering Guide

{% hint style="info" %}
[**View RoboSense Airy Lite Compact 360° × 45° Digital LiDAR for Robotics on OpenELAB**](https://openelab.io/products/robosense-airy-lite-lidar-compact360?variant=45662120935622)

**Model / option:** Only LiDAR · **SKU:** `RS-Airy-Lite`
{% endhint %}

## Product overview

### Product and scope <a href="#product-and-scope" id="product-and-scope"></a>

**RoboSense Airy Lite is a 24-channel, 360° × 45° Ethernet LiDAR with a built-in IMU.** The assigned `RS-Airy-Lite` option is **Only LiDAR**; the accessory-only and sensor-plus-accessory options are separate selections. Obtain a matched Airy Lite cable/power assembly before bench use. This guide covers the **100BASE-TX network platform**, using the actual `RSAIRYLITE_ETH` decoder, rather than the separate SPI/serial implementations. [Official manual](https://robosense-robotics.github.io/product-manual/en/AiryLite/), [exact selection](https://openelab.io/products/robosense-airy-lite-lidar-compact360).

Its small rotating head provides a forward/upward-biased vertical envelope from −11.5° to +33.5°. The mechanical frame also has an expected periodic scan gap; a missing sector is not automatically packet loss.

## Applications

Use Airy Lite for compact mobile-platform mapping, planar-obstacle contour plus height observation and short/mid-range perception. Keep the mounting height and vertical envelope explicit: it is not the 0–90° hemispherical Airy 96. A low obstacle can fall between vertical channels or below the nearest downward beam even if its distance is inside the nominal range.

At 10 Hz, the manufacturer reports an approximately 30° gap in roughly one of every ten frames. Compare an accumulated stationary scene with individual frames before treating that pattern as missing Ethernet packets. A moving robot needs proper timing and motion compensation; accumulating points without accounting for motion can make walls appear thicker. [Manual FOV, scanning and troubleshooting](https://robosense-robotics.github.io/product-manual/en/AiryLite/).

## Specifications

### Hardware and technical documents <a href="#hardware-and-technical-documents" id="hardware-and-technical-documents"></a>

| Parameter                            | Airy Lite Ethernet platform                                      |
| ------------------------------------ | ---------------------------------------------------------------- |
| Channels / FOV                       | 24; 360° horizontal,−11.5° to +33.5° vertical                    |
| Sampling                             | 0.6° horizontal, about 1.96° vertical;10 Hz                      |
| Point rate / returns                 | 144,000 points/s; single strongest return                        |
| Range                                | Maximum 60 m;10% NIST target: 40 m central band,30 m outer bands |
| Central range band                   | −0.25° to +22.25° vertical                                       |
| Outer range bands                    | −11.5° to −0.25° and +22.25° to +33.5°                           |
| Blind zone                           | <0.1 m                                                           |
| Typical accuracy, channels 7–18      | 0–10 m: 0.5 cm;10–40 m: 1 cm                                     |
| Typical accuracy, channels 1–6/19–24 | 0–30 m: 1 cm;30–40 m: 1.5 cm                                     |
| Supply / stated power                | 9–24 V DC;6 W, environment dependent                             |
| Interface / timing                   | 100BASE-TX UDP; GPS, PTP, gPTP                                   |
| Body / mass                          | H 65 × W 64 × D 72.5 mm including cable outlet;<250 g sensor     |
| Environment                          | −20 to +60 °C operating;−40 to +85 °C storage; IP67 sensor       |
| Optical safety                       | Class 1 intact product                                           |

The range bands are tested at normal temperature,100 klux and 10% NIST diffuse target. The accuracy values use a 50% NIST target and vary with channel, range and environment. These are not target-independent detection guarantees or a blanket half-centimeter mapping claim. [Manual specification table/footnotes](https://robosense-robotics.github.io/product-manual/en/AiryLite/).

## Hardware and connections

### Keyed 11-pin interface

The official connector drawing identifies pin 1 beside the locating slot and shows the pin 1–pin 11 winding sequence. Use that exact mating-face orientation; do not number by wire colors alone. The drawing was visually inspected.

| Sensor-side pin | Signal                             |
| --------------- | ---------------------------------- |
| 1 /2            | Ethernet RX+ /RX−                  |
| 3 /4            | Ethernet TX+ /TX−                  |
| 5,8             | GND                                |
| 6,7             | VIN,9–24 V                         |
| 9               | GPS PPS,3.3 V positive pulse input |
| 10              | Reserved; leave unconnected        |
| 11              | GPS GPRMC, RS232 input             |

[Manual interface definition](https://robosense-robotics.github.io/product-manual/en/AiryLite/#331-aviation-plug-interface-and-definitions). The PPS and GPRMC electrical standards are different. In particular, **Airy Lite PPS is 3.3 V**, not the wider PPS range of Airy 96. Pin 10 is reserved here; do not repurpose it as another model's sync output. Use 9600 baud 8N1 for GPRMC,20–200 ms PPS High each second, and the documented message timing after PPS. Initial capture needs no external synchronization wiring. PTP/gPTP use Ethernet and require compatible master transport/domain/profile; verify lock rather than assuming clock correctness.

### Mechanical and thermal installation

The current manual specifies four M3 screws with 4–5 mm protrusion through the mounting surface,6.6±0.5 kgf·cm torque, and mounting bosses flat within 0.05 mm. Two Φ2.5 mm locating pins must not protrude more than 1.5 mm. These limits belong to Airy Lite, not Airy 96. Check the received revision/drawing before fabrication. Leave the 6 mm cable at least 30 mm bend radius, avoid tensile loading and keep the base ventilation holes clear. [Manual installation](https://robosense-robotics.github.io/product-manual/en/AiryLite/#32-mechanical-installation).

A conductive aluminum bracket, thermal interface and suitable airflow are part of the installation: the manual recommends bracket conductivity>90 W/(m·K), surface area ≥10,000 mm² and interface conductivity ≥3 W/(m·K). Do not clamp the plastic optical cover or sandwich the body under preload. Keep all brackets/cables outside the optical field.

### Geometry and data interpretation

Use the DIFOP vertical/horizontal calibration and IMU calibration. Nominally uniform 1.96° spacing is not a replacement for per-device angles. Cloud origin is at the center of the base; retain ring/time for a consumer requiring them. The manual's MSOP header table labels byte 5 as status, despite being in the measurement section. The reviewed decoder treats those two header bytes as reserved; the diagnostic example below checks **length and magic only** rather than inventing a discriminator. [Manual protocol](https://robosense-robotics.github.io/product-manual/en/AiryLite/), [actual decoder](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/driver/decoder/decoder_RSAIRYLITE_ETH.hpp).

## Software and development resources

### Development software and recovery <a href="#development-software-and-recovery" id="development-software-and-recovery"></a>

The reviewed `rslidar_sdk` and decoder submodule support `RSAIRYLITE_ETH`. Use the documented Ubuntu 22.04/ROS2 Humble baseline, with PCL,`yaml-cpp`≥0.5.2,`libpcap`≥1.7.4 and official `rslidar_msg`. Do not keep the shipped `RSM1` model merely because packets arrive. [SDK README](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/README.md).

| Stream                   | Factory host destination / UDP payload                            |
| ------------------------ | ----------------------------------------------------------------- |
| MSOP cloud               | 192.168.1.102: 6699 /1280 bytes, about 2.667 ms                   |
| DIFOP calibration/status | 192.168.1.102: 7788 /540 bytes, about 100 ms                      |
| IMU                      | 192.168.1.102: 6688 /51 bytes, about 5 ms                         |
| Sensor address           | 192.168.1.200; observe actual configuration if previously changed |

[Manual network and packet tables](https://robosense-robotics.github.io/product-manual/en/AiryLite/). An MSOP contains sixteen 74-byte blocks of 24 channels, with 0.01° azimuth and 0.005 m range units. Only the lower 14 range bits are distance; the upper two are reserved feature markers. The actual decoder applies `raw & 0x3FFF`. A generic 16-bit range interpretation produces false long distances. [Exact decoder](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/driver/decoder/decoder_RSAIRYLITE_ETH.hpp).

RSView supports live display, PCAP recording/replay and CSV export; the manual notes LAS export from 3.1.3. Use a build supporting the Airy Lite profile, not a merely similar Airy profile. PCAPNG is not accepted for replay. The public manual excludes upgrade/diagnostic protocols; obtain an exact serial/revision firmware package from RoboSense instead of constructing flash commands.

### SDK configuration, recording and replay behavior

The pinned SDK uses one shared `common` block and one `lidar` list entry per sensor. For **Airy Lite Ethernet**, keep **`lidar_type:RSAIRYLITE_ETH`** and the model-specific network/packet revision above. The receive-port baseline is **6699/7788/6688**; these are not permission to transfer a cable, wake signal or decoder from a similar model.

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

### Airy Lite calibration, IMU and firing-time fields

The Ethernet profile uses a **22-byte MSOP header, sixteen 74-byte blocks and 74-byte tail**. The 10-byte header time at offset 6 is 6-byte seconds plus 4-byte microseconds; model bytes at 16/17 identify network-platform Airy Lite (`0x0C`) and 24 channels (`0x04`). Each block's azimuth precedes 24 range/reflectivity triples. The published header's data-type comment conflicts with its measurement context, so keep the bounded shape check above and the actual decoder rather than use that comment to classify packets.

| DIFOP byte offset / length         | Actual readback / engineering use                                                                                                       |
| ---------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| 6/4, 10/4, 14/4                    | Mainboard, baseboard and motor firmware identifiers                                                                                     |
| 18/4, 22/4, 26/6; 32/2, 34/2, 36/2 | Sensor/target IPv4, MAC and MSOP/DIFOP/IMU ports                                                                                        |
| 49/6                               | Device serial identifier                                                                                                                |
| 94/1, 95/1; 96/10                  | Sync mode, success state and time                                                                                                       |
| 106/1                              | GPS GPRMC baud selector; `0x03` = 9600 baud (default); full map below                                                                   |
| 311/2, 313/2                       | FOV start/end; table gives 0.01° precision but contradictory range wording; preserve raw readback and the exact firmware interpretation |
| 315/2                              | Phase-lock angle; table states 0–360 with 1° precision                                                                                  |
| 342/2                              | Motor speed, raw × 0.1 RPM                                                                                                              |
| 348/48 and 396/3                   | 24 unsigned vertical magnitudes at 0.01° plus separate sign bits                                                                        |
| 399/48 and 447/3                   | 24 horizontal corrections and their separate sign bits                                                                                  |
| 473/28                             | IMU-to-LiDAR quaternion qx/qy/qz/qw and XYZ float32 transform                                                                           |
| 508/2, 526/2                       | Mainboard/baseboard input-voltage readings, raw/100 V                                                                                   |

These DIFOP numerical fields use the appendix's big-endian interpretation. Angle sign 0 is positive and 1 negative; do not cast magnitude/sign fields as ordinary two's-complement int16. At offset 94, sync mode **0/1/2/3/4** means GPS/E2E-L4/P2P/gPTP/E2E-L2, while offset 95 is **0 not synchronized / 1 synchronized**. Preserve both values. [Manual §4.3 and Appendix B](https://robosense-robotics.github.io/product-manual/en/AiryLite/).

The GPRMC selector map at byte 106 is `00:1200`, `01:2400`, `02:4800`, `03:9600`, `04:14400`, `05:19200`, `06:38400`, `07:43000`, `08:57600`, `09:76800`, `0A:115200`, `0B:128000`, `0C:230400`, `0D:256000`, `0E:460800`, `0F:921600`, `10:1382400` baud (selector codes are hexadecimal). `43000` is the value printed for `0x07`; it is not silently corrected to another common baud rate. Match the actual GPS transmitter and supported firmware readback. The FOV table simultaneously prints a range of “0–359” and 0.01° precision for bytes 311/313, without resolving raw-versus-degree range. Do not derive a new accepted raw range or clamp/write setting from that inconsistent wording. These rows describe readback, not a field-write procedure. [Manual §4.3.3, Table 11](https://robosense-robotics.github.io/product-manual/en/AiryLite/).

| IMU byte offset / length | Type, scale and selector interpretation                                                                                             |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------------------------- |
| 0/4; 5/1                 | Header `5A FF 55 AA`; data type 2                                                                                                   |
| 6/10                     | UTC timestamp: 6-byte seconds and 4-byte microseconds                                                                               |
| 16/4, 20/4, 24/4         | Float32 acceleration X/Y/Z already in m/s²                                                                                          |
| 28/4, 32/4, 36/4         | Float32 gyro X/Y/Z already in rad/s                                                                                                 |
| 40/4                     | Signed internal temperature, raw × 0.01 °C; stated operating reading range −40 to +105 °C                                           |
| 44/1                     | Output rate: 0/1/2/3 = 25/50/100/200 Hz; 3 is default                                                                               |
| 45/1                     | Accelerometer full scale: 0/1/2/3 = ±2/±4/±8/±16 g; 1 is default                                                                    |
| 46/1                     | Gyro full scale: 0/1/2/3 = ±250/±500/±1000/±2000 degrees/s; 1 is default                                                            |
| 47/2                     | Unsigned packet sequence 0–65535                                                                                                    |
| 49/2                     | CRC16 over header through packet count; the reviewed table does not establish the CRC variant/polynomial/init/reflection parameters |

The selectors identify the configured sensor range; they do not change the table's transmitted float axes into raw ADC counts. Do not multiply acceleration by g or convert an already-rad/s gyro a second time. Preserve the signed temperature and sequence-wrap semantics. [Manual §4.3.4, Table 12](https://robosense-robotics.github.io/product-manual/en/AiryLite/).

The **51-byte IMU** carries timestamp at 6, acceleration XYZ at 16/20/24 in m/s² and gyro XYZ at 28/32/36 in rad/s, followed by temperature, output-rate/range selectors, sequence and CRC16. Rate selectors 0/1/2/3 mean 25/50/100/200 Hz (200 Hz default); default accelerometer/gyro ranges are ±4 g and ±500 degrees/s. The terminal CRC16 covers header through sequence. A nonzero IMU count does not validate CRC, axis calibration or time lock.

Appendix D groups channel firing delays in µs as **00–05: 0; 06–11: 21; 12–17: 64; 18–23: 107**. These offsets matter for moving-platform deskew and are not derived by dividing a frame interval by 24. Use the pinned decoder's full timestamp/azimuth behavior with the actual calibration rather than apply this short table twice.

### Native driver API and callback backpressure

A native C++ integration uses the pinned `LidarDriver<PointCloud>` API: register the free-cloud/completed-cloud callbacks and exception callback, populate `RSDriverParam` with this model's decoder/input settings, check `init()` and `start()` Boolean results, then call `stop()` to join the acquisition threads. `regPacketCallback` exposes packets separately from decoded clouds, while `getTemperature`, `getDeviceInfo` and `getDeviceStatus` return a Boolean indicating whether the requested information is available. A valid API method does not mean every model populates every field. [Public native API](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/api/lidar_driver.hpp).

The user's callbacks execute on the driver's decoding thread. Queue the completed cloud for a separate processing thread and recycle buffers after consumption; avoid mapping, file compression or slow network calls inside the callback. The documented consequence of blocking is **`ERRCODE_PKTBUFOVERFLOW` and discarded packets**, which can resemble a bad Ethernet link. Separate link/capture loss from application backlog before changing the sensor's power or calibration. Native `decodePacket` can consume an externally supplied packet source, but still needs the correct model framing and calibration. libpcap is needed for native PCAP input, Eigen for internal transforms, and PCL/Boost for the optional visualization tool; they are not all intrinsic requirements of every receive-only application. [Thread ownership and buffer queues](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/doc/intro/03_thread_model.md), [native dependencies and demo build options](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/README.md).

### Airy Lite source-layout boundaries and service-life care

The public DIFOP table labels bytes **501–535** reserved yet separately places input-voltage readings at **508/526**. The pinned `RSAIRYLITEETHDifopPkt` resolves that region as a status/scroll structure beginning at 508, with `vdc_top_vbus` and `volatge_bot_vbus` at those respective positions. Its receive-only parser also places calibration arrays at **348/399**, agreeing with the manual's geometry region. Keep the manual's versioned meanings and the decoder's actual structure together; a generic “reserved” label is not permission to overwrite those bytes. Firmware/network fields retained as reserved by a decoder may still be described by the manual, so a field map is not a promise that the SDK exposes every register as an API.

The MSOP header counter/CRC region and IMU CRC16 are validation fields, but the source reviewed here does not establish a named CRC16 variant to reproduce independently. The original shape-check program therefore reports magic/length only. The official decoder's per-channel timestamp uses its block iterator and Appendix D channel delays together with DIFOP calibration and azimuth interpolation; a simple 1.96° grid or equal subdivision of the frame is insufficient. The native Cartesian relation also includes this model's optical-center offsets and axis convention; consume the calibrated decoder output before a measured robot-frame transform. [Exact layout and geometry implementation](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/driver/decoder/decoder_RSAIRYLITE_ETH.hpp).

For storage, protect the connector/cover in a dry indoor, noncorrosive environment within the storage rating; the manual recommends inspecting product and packaging every **three months**. Use cushioned moisture-resistant packaging for transport and inspect delivery damage before use. For cleaning, first remove loose mud/solid material with clean water instead of dragging it over the optical cover; use a clean dust-free cloth with a small amount of mild neutral cleaner, remove residue and dry gently. Keep the base ventilation unblocked. Preserve a baseline PCAP/configuration before fault recovery and obtain manufacturer authorization/instructions before return shipment. [Official care and after-sales chapters6–7](https://robosense-robotics.github.io/product-manual/en/AiryLite/).

## Getting started <a href="#getting-started" id="getting-started"></a>

### First point cloud

1. Confirm the sensor's network-platform identity and obtain its matched cable and approved 9–24 V supply. Mount on the thermal bracket, connect with power off, and leave optional sync branches insulated.
2. Set a dedicated host adapter to **192.168.1.102/24**, which matches the factory destination; the sensor is `.200`. Energize the approved power path and verify link.
3. Capture on that interface in Wireshark. Observe ARP source/target addresses and UDP destination ports. If the device was changed, record those observed endpoints before editing host settings.
4. Open a supporting RSView build, select Airy Lite/network profile and receive 6699/7788. Check a fixed diffuse target, save a short **PCAP**, then replay it.
5. Compare individual frames and a short accumulation. Account for the documented periodic 30° gap before diagnosing loss.

**Expected result:** an updating 24-channel scene spanning the asymmetric 45° vertical envelope, and replay with coherent geometry. Packet reception alone does not establish calibration or time lock. [Manual quick connection/RSView](https://robosense-robotics.github.io/product-manual/en/AiryLite/).

### Original packet-shape check

Close RSView/ROS first. Save as `airylite_packets.py` and run `python3 airylite_packets.py` on the configured host. This program listens eight seconds and sends nothing:

```python
import collections
import selectors
import socket
import time

ports = {6699: 1280, 7788: 540, 6688: 51}
counts = collections.Counter()
unexpected = collections.Counter()
selector = selectors.DefaultSelector()
sockets = []
try:
    for port in ports:
        sock = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
        sockets.append(sock)
        sock.bind(("192.168.1.102", port))
        sock.setblocking(False)
        selector.register(sock, selectors.EVENT_READ, port)
    finish = time.monotonic() + 8
    while time.monotonic() < finish:
        for key, _ in selector.select(0.2):
            data, peer = key.fileobj.recvfrom(65535)
            port = key.data
            counts[port] += 1
            if len(data) != ports[port] or data[:4] != bytes.fromhex("5a ff 55 aa"):
                unexpected[port] += 1
            if counts[port] == 1:
                print(port, peer, "payload", len(data), "header", data[:8].hex())
    for port in ports:
        print(port, "received", counts[port], "unexpected", unexpected[port])
finally:
    selector.close()
    for sock in sockets:
        sock.close()
```

**Expected result:** nonzero cloud/status counts with expected payload lengths and common header; IMU appears if enabled. Unexpected packets require a model/protocol check. This is not a CRC, calibration or accuracy test. An occupied UDP port or a host address mismatch can prevent reception.

### ROS2 Humble build

Use a fresh workspace after establishing the GUI/packet checkpoint:

```bash
mkdir -p ~/airylite_ws/src
cd ~/airylite_ws/src
git clone https://github.com/RoboSense-LiDAR/rslidar_sdk.git
cd rslidar_sdk
git checkout 8b4b4b7ff910799260347821084c59e1c73d50d5
git submodule update --init --recursive
cd ~/airylite_ws/src
git clone https://github.com/RoboSense-LiDAR/rslidar_msg.git
```

Edit `rslidar_sdk/config/config.yaml`: `common.msg_source:1`, `driver.lidar_type:RSAIRYLITE_ETH`, `msop_port:6699`, `difop_port:7788`, `imu_port:6688`, `send_point_cloud_ros:true`, frame `rslidar` and topic `/rslidar_points`. Inspect `min_distance`: the generic 0.2 m filter hides closer returns. Set application limits deliberately. For per-point ring/time, edit CMake's direct `set(POINT_TYPE ...)` to `XYZIRT`; a launch parameter does not alter the compiled structure. [Configuration](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/config/config.yaml), [CMake](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/CMakeLists.txt).

```bash
cd ~/airylite_ws
source /opt/ros/humble/setup.bash
colcon build --symlink-install --cmake-args -DENABLE_IMU_DATA_PARSE=ON
source install/setup.bash
ros2 launch rslidar_sdk start.py
```

In another sourced terminal:

```bash
ros2 topic hz /rslidar_points
ros2 topic hz /rslidar_imu_data
ros2 topic echo /rslidar_points --once --field header
```

**Expected result:** current cloud and enabled IMU publications with the intended frame. Choose RViz Fixed Frame `rslidar` unless a validated transform exists. For recorded diagnosis, set `msg_source:3` and the actual `pcap_path` while retaining the exact model and ports. [Live/replay instructions](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/README.md).

## Troubleshooting and FAQs

### FAQs <a href="#faqs" id="faqs"></a>

| Symptom                          | Model-specific check                                                                             |
| -------------------------------- | ------------------------------------------------------------------------------------------------ |
| Motor runs, no cloud             | Host target `.102`, ports, firewall scoped to dedicated adapter, MSOP versus status-only traffic |
| Periodic missing sector          | Documented 30° gap about one frame in 10; compare capture counts and accumulation                |
| Range jumps unexpectedly         | Lower 14-bit range mask,0.005 m units and actual AiryLite Ethernet decoder                       |
| Wrong vertical geometry          | Per-device DIFOP angles, model selection and 24 channels, not Airy 96                            |
| No IMU topic                     | Port 6688 plus `ENABLE_IMU_DATA_PARSE=ON`; port setting alone is insufficient                    |
| Boot repeats                     | Input power/polarity, flatness, screw protrusion and torque; avoid distorting housing            |
| No GPS lock                      | GPRMC RS232 versus PPS 3.3 V,9600 baud 8N1, common ground, PPS timing and valid fix              |
| Packets in capture but no RSView | Correct model/network profile, PCAP format, host destination and supporting viewer build         |

**Can Airy 96 settings be reused?** Network port numbers overlap, but channels, FOV, packet sizes, PPS limit and pin 10 function differ. Use this model's configuration.

**Does the SDK's 100 m decoder maximum prove 100 m range?** No; it is a software acceptance bound. The product specifies 60 m maximum and reflectivity/FOV-qualified shorter distances.

Clean loose mud/particles before wiping the optical cover to avoid scratches. Keep ventilation clear, store protected and dry, and inspect cable strain/connector sealing. Preserve PCAP/configuration before recovery; obtain exact firmware through manufacturer support rather than an undocumented upgrade protocol. [Manual maintenance/faults](https://robosense-robotics.github.io/product-manual/en/AiryLite/).

## Downloads and technical documents

| Resource                                                                                                                                                                                                                                                                                      | Exact scope                                                                                                                  |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| [Airy Lite official manual](https://robosense-robotics.github.io/product-manual/en/AiryLite/)                                                                                                                                                                                                 | Safety, specification footnotes, keyed interface, mounting, RSView, packet layout, calibration and emission-delay appendices |
| [Connector face drawing](https://robosense-robotics.github.io/product-manual/assets/airylite-en/3.3.1.jpg)                                                                                                                                                                                    | Manufacturer drawing, rights retained; visually inspected pin 1/locating slot                                                |
| [Structural drawing](https://robosense-robotics.github.io/product-manual/assets/airylite-en/C.jpg)                                                                                                                                                                                            | Exact Airy Lite installation envelope                                                                                        |
| [SDK source](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/README.md) / [Ethernet decoder](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/driver/decoder/decoder_RSAIRYLITE_ETH.hpp) | Actual `RSAIRYLITE_ETH` model and packet handling                                                                            |
| [RoboSense resources](https://www.robosense.ai/en/resources)                                                                                                                                                                                                                                  | Model-matched viewer/firmware/support resources                                                                              |

Original diagrams are linked with attribution rather than recreated. Preserve the manufacturer's connector view and the shipped drawing revision when designing a harness.

## References and validation

### Sources and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

Reviewed 24 November 2026: exact `RS-Airy-Lite` sensor-only option, full official AiryLite manual and its appendices, visually inspected connector drawing, and the actual SDK/submodule Ethernet decoder. The MSOP-table discriminator ambiguity is bounded by checking only verified packet shape and using the official decoder.

**SDK compilation, ROS/RSView execution, packet-monitor execution, firmware update and electrical/physical tests: not run.** The packet-check example is original and syntax checked.

* [Airy Lite official manual and appendices](https://robosense-robotics.github.io/product-manual/en/AiryLite/) — current 24 Nov 2026; Ethernet 24 channel platform.
* [RoboSense ROS2 SDK model/build instructions](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/README.md) — commit 8b4b4b7ff910799260347821084c59e1c73d50d5.
* [AiryLite Ethernet packet decoder](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/driver/decoder/decoder_RSAIRYLITE_ETH.hpp) — commit 897b14d3bdb6186a75df27ba51b65b5bd5557723.
* [SDK model/port/filter configuration](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/config/config.yaml) — commit 8b4b4b7ff910799260347821084c59e1c73d50d5.
* [Point type and IMU compile option](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/CMakeLists.txt) — commit 8b4b4b7ff910799260347821084c59e1c73d50d5.
* [Exact Airy Lite sensor-only selection](https://openelab.io/products/robosense-airy-lite-lidar-compact360) — catalog 23 Nov plus live public page 24 Nov.

### Additional established references

* [Official ROS SDK](https://github.com/RoboSense-LiDAR/rsLiDAR_sdk)

### Supporting resource links

* [Low-level driver](https://github.com/RoboSense-LiDAR/rs_driver)
