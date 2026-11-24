---
description: >-
  Wire the exact 12 V M 1 Plus kit and automotive-Ethernet interface, verify
  wakeup and live packets, capture/replay a cloud and select a packet-matched
  RSM1 ROS2 decoder.
layout:
  width: default
  title:
    visible: false
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
  anchors:
    visible: true
---

# Robosense M1 Plus

{% hint style="info" %}
[**View RoboSense M1 Plus 200 m Automotive-Grade MEMS Solid-State LiDAR on OpenELAB**](https://openelab.io/products/robosense-m1-plus-solid-state-lidar?variant=45700976804038)

**Model / option:** M1 PLUS (12 V) - LiDAR with Accessory Kit · **SKU:** `RS-M1P-12-Kit`
{% endhint %}

## Product overview <a href="#product-overview" id="product-overview"></a>

**This guide covers RoboSense M1 Plus 12 V with accessories, SKU `RS-M1P-12-Kit`.** The MEMS sensor's **1000BASE-T1 automotive Ethernet** requires the matching harness/interface box before a normal computer Ethernet adapter. An RJ45 patch cable alone cannot replace that physical-layer conversion.

The sold kit includes the 12 V LiDAR,3.5 m Ethernet/power harness, power adapter/cord, E1R power interface box, RJ45 cable and six listed M4 fasteners. Sensor-only, accessory-only and 24 V packages on the same store page are different options. [Exact option and BOM](https://openelab.io/products/robosense-m1-plus-solid-state-lidar?variant=45700976804038).

The hardware/packet baseline below is the OEM **RS-LiDAR-M1P User Guide v1.3.0,21 December 2022**. Current sales specifications can describe a later performance revision; keep those apart from this manual's packet, voltage and wakeup requirements. [Original manufacturer PDF](https://cdn.robosense.cn/20240322145019_37549.pdf).

## Applications <a href="#applications" id="applications"></a>

Use M1 Plus for forward-sector perception, road-scene point collection and vehicle-sensor fusion research. Its 120° horizontal coverage does not observe behind the platform. The nominal 25° vertical sector also needs correct pitch and a measured origin to see nearby ground or overhead structure.

For initial integration, record a static facade or planar board at known distance, then replay the same capture after each decoder/configuration change. For a moving platform, synchronize the sensor clock and preserve per-point timing before judging registration error. GAZE/region-of-interest sampling changes local density; it is not uniform 0.1° resolution across every part of the view.

A component's automotive test/certification or environmental rating does not by itself certify a complete autonomous vehicle. This guide establishes a measurement/data path rather than an unattended driving function.

## Specifications

### Key specifications <a href="#key-specifications" id="key-specifications"></a>

| Parameter                     | Documented 12 V M1P baseline                                                           |
| ----------------------------- | -------------------------------------------------------------------------------------- |
| Method / wavelength           | MEMS time-of-flight,905 nm, Class 1 intact-product laser classification                |
| Horizontal / vertical FOV     | 120°(−60° to +60°) /nominal 25°(−12.5° to +12.5°)                                      |
| Range                         | 0.5–200 m;180 m at 10% NIST target reflectivity                                        |
| Range precision               | ±5 cm,1σ, manual 10–100 m/50%NIST conditions                                           |
| Average angular sampling      | 0.2° H/V in the referenced guide; nonuniform over the full sector                      |
| Frame / point rate,2022 guide | 10 Hz; about 750,000 points/s single return,1,500,000 dual                             |
| Data link                     | 1000BASE-T1 sensor side; UDP                                                           |
| Supply / steady power         | 9–16 V DC for 12 V hardware;15 W under stated stable test conditions                   |
| Outline                       | 110 mm length × 111 mm width × 45 mm height in the referenced drawing                  |
| Environment                   | −40 to 85 °C operating, forced convection for extended operation;−40 to 105 °C storage |
| Ingress rating                | IP67/IP6K9K under manufacturer conditions                                              |

[M1P v1.3.0 §§1–2](https://cdn.robosense.cn/20240322145019_37549.pdf). The manual explains that the five vertically staggered subfields do not form a simple uniform rectangular scan; use actual per-point angles rather than inventing a regular ring model.

The current store lists 787,500/1,575,000 points/s,10/20 Hz and 690±20 g, while the 2022 guide lists 750,000/1,500,000,10 Hz and about 0.75 kg. Those are **revision-specific values**, not interchangeable settings or a reason to modify the decoder. Confirm delivered hardware/firmware and the matching current specification before a throughput or weight-critical design. The 12 V electrical path remains explicitly 9–16 V in the cited baseline. [Current listing](https://openelab.io/products/robosense-m1-plus-solid-state-lidar).

| Packet/network baseline      | Value                                                            |
| ---------------------------- | ---------------------------------------------------------------- |
| Sensor / unicast destination | 192.168.1.200 /192.168.1.102, mask 255.255.255.0                 |
| MSOP / DIFOP host port       | 6699 /7788                                                       |
| MSOP / DIFOP UDP payload     | 1210 /256 bytes                                                  |
| MSOP header                  | `55 aa 5a a5`,32-byte header,25 × 47-byte blocks,3-byte tail     |
| DIFOP header                 | `a5 ff 00 5a 11 11 55 55`                                        |
| Range / angular units        | 5 mm per range count;0.01° per angle count with 32768 angle bias |

[Manual §2](https://cdn.robosense.cn/20240322145019_37549.pdf); [reviewed decoder constants](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/driver/decoder/decoder_RSM1.hpp). Link bandwidth, UDP rate and decoded frame rate are distinct quantities.

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

### Use the matched 12 V interface kit

With all sources disconnected, check the 12 V label and the supplied interface-box/cable part numbers. Connect the LiDAR to its automotive-Ethernet/power harness, the harness to the matched box and the box's ordinary RJ45 port to the host. Connect the approved power adapter through the documented kit path. Do not attach an RJ45-to-two-wire improvisation to the sensor's automotive pair.

The OEM manual's TE connector drawing specifies **TE2387351-1**. Read it from the sensor-face view in Appendix C; connector numbering is not the same as the visually opposite cable view.

| TE terminal | Function and boundary                         |
| ----------- | --------------------------------------------- |
| 1           | GND                                           |
| 2           | Wakeup/KL15                                   |
| 4           | Battery +,9–16 V on this 12 V variant         |
| 3,5,6       | Unassigned in the cited drawing; leave unused |
| D1          | TRX\_N, 1000BASE-T1                           |
| D2          | TRX\_P, 1000BASE-T1                           |

[Original connector face/table, PDF page 37](https://cdn.robosense.cn/20240322145019_37549.pdf). The wakeup pin is **not 3.3 V logic**: manual §3.3 specifies 7–16 V for High and 0–2 V for Low. Supply presence can leave the device in Sleep until wakeup is correctly asserted through the approved kit. Do not add a bare-wire bridge from these numbers alone; match the actual harness/state-machine wiring.

### Mount, cool and protect the optical path

Use the OEM Appendix C dimensioned drawing for base holes, engagement and connector clearance. Choose screws from the actual bracket stack; the package fastener count is not a screw-depth specification. Avoid bracket stress through the housing and provide cable strain relief. Keep the aperture clear and expose the intended heat-dissipation path. The manual requires forced convection for prolonged high-temperature use; ambient range is not permission to enclose a 15 W sensor without thermal analysis. [Manual §§1,3 and Appendix C](https://cdn.robosense.cn/20240322145019_37549.pdf).

### Clock profile and coordinates

The referenced default firmware supports **gPTP/IEEE 802.1AS**. The manual says other PTP support requires a suitable manufacturer firmware/configuration. Do not take its generic PTP discussion as proof every unit supports every transport/profile. A GPS-disciplined setup feeds the external gPTP grandmaster; it is not direct GPS serial input on an invented M1P GPIO.

On a Linux host, `ethtool -T ACTUAL_INTERFACE` is a read-only capability check; hardware timestamp/PHC support matters for gPTP. Inspect actual sync mode/status in DIFOP and verify the master before fusing sensors. A free-running timestamp after master loss is not continued external synchronization. Store a measured sensor-to-base transform with the capture. [Manual §4](https://cdn.robosense.cn/20240322145019_37549.pdf).

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### Decoder choice follows the packet revision

The M1P manual explicitly selects **RSM1** in RSView. The pinned `DecoderRSM1` uses the same 1210-byte MSOP,256-byte DIFOP, header constants,25 blocks and 5 channels per block documented by that M1P revision. This is the source basis for the RSM1 path; it is not a blanket statement that every later M1/M1P or jumbo-packet firmware is identical. Stop and recheck if the observed payloads differ. [Manual Appendix A](https://cdn.robosense.cn/20240322145019_37549.pdf), [decoder](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/driver/decoder/decoder_RSM1.hpp).

For Ubuntu 22.04/ROS2 Humble use the pinned `rslidar_sdk` and its matching `rs_driver` submodule plus `rslidar_msg`. Dependencies include PCL, yaml-cpp and libpcap. Set `lidar_type:RSM1`, MSOP 6699, DIFOP 7788 and the actual sensor's clock policy; do not select `RSM1_JUMBO` just because the physical Ethernet link is gigabit.

RSView on Windows 64-bit provides the shortest manual-backed live capture path. Current official downloads are listed in the M1 Plus resource center; obtaining executables/current exact firmware can require the manufacturer's request form. Use the approved installed Viewer build rather than inventing an unobserved binary URL. [Manufacturer resource center](https://www.robosense.ai/en/resources-11), [SDK build instructions](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/README.md).

### SDK configuration, recording and replay behavior

The pinned SDK uses one shared `common` block and one `lidar` list entry per sensor. For **M1P**, keep **`lidar_type:RSM1`** and the model-specific network/packet revision above. The receive-port baseline is **6699/7788; no IMU port established for this profile**; these are not permission to transfer a cable, wake signal or decoder from a similar model.

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

### M1P packet fields, return pairing and status

For the reviewed M1P manual v1.3.0, the **1210-byte** measurement payload is **32-byte header + 25 × 47-byte blocks + 3 reserved tail bytes**. Header bytes begin `55 AA 5A A5`; sequence numbering starts at 1 for each frame. The header carries protocol revision, return mode, time-sync mode, a 6-byte seconds + 4-byte microseconds timestamp and MEMS temperature (`raw−80` °C). These fields make a packet-version/counter journal more useful than a payload-length count alone.

Each block starts with a 1-byte microsecond offset from the packet timestamp and `return_seq`, followed by five 9-byte channels. A channel contains big-endian range in 5 mm units, elevation and azimuth in 0.01° units encoded with **32768 bias**, intensity 0–255 and two reserved bytes. Convert each angular integer as `(raw−32768)×0.01°`, then use the documented spherical-to-Cartesian relation. Angles are carried per point; do not substitute a uniform channel-angle table from a spinning scanner. The Viewer appendix says these output measurements are already calibrated and its MEMS correction-file slot is not an additional correction to apply.

Return flags are **0 dual, 4 strongest, 5 last, 6 first** for this revision. Single-return blocks use sequence 0. In dual mode, odd/even MSOP packets alternate closer/farther returns, identified by block sequence 1/2; pair them by frame/counters/time rather than treating every received packet as a different physical scan. [Manual §§2.1–2.2 and Appendix A](https://cdn.robosense.cn/20240322145019_37549.pdf), [matching RSM1 decoder](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/driver/decoder/decoder_RSM1.hpp).

The 256-byte output-only DIFOP starts `A5 FF 00 5A 11 11 55 55`. Useful byte offsets are **9** scan frequency; **10/14** source/destination IPv4; **18** MAC; **24/26** MSOP/DIFOP ports; **28/33** board firmware fields; **54** return mode; **55/56** sync mode/status; **57** 10-byte time; **67** input-voltage field; **136** diagnostic status. Sync-mode values 0/1/2/3 mean internal clock/PPS reset/PTP/gPTP; status 0/1/2 means unsynchronized/synchronized/timed out. Read and retain these fields before interpreting a good-looking cloud as time-aligned. Do not invent a voltage scale or fault-bit decoder from the field name where the reviewed table does not establish it.

### Native driver API and callback backpressure

A native C++ integration uses the pinned `LidarDriver<PointCloud>` API: register the free-cloud/completed-cloud callbacks and exception callback, populate `RSDriverParam` with this model's decoder/input settings, check `init()` and `start()` Boolean results, then call `stop()` to join the acquisition threads. `regPacketCallback` exposes packets separately from decoded clouds, while `getTemperature`, `getDeviceInfo` and `getDeviceStatus` return a Boolean indicating whether the requested information is available. A valid API method does not mean every model populates every field. [Public native API](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/api/lidar_driver.hpp).

The user's callbacks execute on the driver's decoding thread. Queue the completed cloud for a separate processing thread and recycle buffers after consumption; avoid mapping, file compression or slow network calls inside the callback. The documented consequence of blocking is **`ERRCODE_PKTBUFOVERFLOW` and discarded packets**, which can resemble a bad Ethernet link. Separate link/capture loss from application backlog before changing the sensor's power or calibration. Native `decodePacket` can consume an externally supplied packet source, but still needs the correct model framing and calibration. libpcap is needed for native PCAP input, Eigen for internal transforms, and PCL/Boost for the optional visualization tool; they are not all intrinsic requirements of every receive-only application. [Thread ownership and buffer queues](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/doc/intro/03_thread_model.md), [native dependencies and demo build options](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/README.md).

### Controlled PTP/gPTP timing and GPS-master topology

For **M1P**, time-master commissioning is separate from first cloud acquisition. The M1P manual says default firmware supports gPTP only; alternate IEEE 1588v2 PTP firmware requires RoboSense confirmation. Its generic MSOP time enum is not proof that the delivered default firmware supports every choice.

1. Use the identified converter and dedicated wired interface, with one deliberately selected clock master. Read interface names and timestamp capability with `ip link` and **`ethtool -T INTERFACE`**. For the documented hardware-timestamped gPTP path, require an actual PHC/capability rather than `none`.
2. Record the installed `ptp4l -v` and `ptp4l -h` output. For gPTP, make a reviewed master configuration matching the values below. For the separately supported PTP path, choose **L2 + E2E**, not the default UDP/IPv4 profile merely because the same tool accepts it.
3. On the isolated test link, run the selected master with the actual interface and reviewed file; the source's hardware gPTP shape is `sudo ptp4l -i INTERFACE -m -H -2 -f ./gptp-master.cfg`. Substitute the identified interface; this is a clock-master operation, not a passive diagnostic. `-S` is a software-timestamp simulation alternative with no promised hardware-level accuracy.
4. Inspect Sync/Follow\_Up and peer-delay traffic in a capture, then the sensor's DIFOP time mode and lock result. A running `ptp4l` process alone is not a synchronized sensor. Verify successful status during an observation window and record any timeout/recovery without changing acquisition calibration.

| Master setting in the reviewed example              | Intended profile value                                                                      |
| --------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| `domainNumber`, `logSyncInterval`                   | **0**, **−3** (nominal Sync interval 125 ms)                                                |
| `network_transport`, `delay_mechanism`              | **L2**, **P2P** for gPTP                                                                    |
| `transportSpecific`, `ptp_dst_mac`                  | **0x1**, **01:80:C2:00:00:0E**                                                              |
| `masterOnly`, `BMCA`                                | **1**, **noop**, a deliberately fixed master role                                           |
| `syncReceiptTimeout`, `neighborPropDelayThresh`     | **3**, **800**, as source profile values; do not relabel them as a measured sensor accuracy |
| `path_trace_enabled`, `follow_up_info`, `asCapable` | **1**, **1**, **true**                                                                      |
| `inhibit_announce`, `inhibit_delay_req`             | Both **1** in the source automotive-style profile                                           |

The sample is a profile to review against the installed linuxptp version, NIC and switch, not a universal production network configuration. In DIFOP, record both selected time method and **0 failed/unsynchronized, 1 success, 2 timeout** state. For M1P these are offsets 55/56; use E1R's own status map above for that model. If the master disappears, M1P's manual says its time continues from the internal clock until power restart; continued numerical timestamps do not establish continued lock.

For GPS-referenced time, the documented topology is **GPS → compatible external gPTP grandmaster → Ethernet/converter → sensor**. Consult that grandmaster's actual GPS connector/electrical/time interface; do not fabricate direct GPS UART/PPS wiring onto an automotive connector. Check grandmaster absolute time as well as the sensor's lock, since a slave can follow a wrong but valid-looking master. [Exact model timing/topology source](https://cdn.robosense.cn/20240322145019_37549.pdf).

### RSView recording, replay, export and measurement

Use a Viewer release supporting the exact **M1P** packet profile. A practical comparison keeps original packets separate from exported points:

1. Verify the live scene, selected decoder/profile, time mode and receive ports. For M1P, the manual uses the **RSM1** profile and says its emitted angles are already calibrated; its MEMS correction slot is not another serial calibration to apply.
2. Start a short raw **PCAP** recording containing measurement and status/calibration traffic; retain serial/firmware, receive configuration and any external time source. **PCAPNG is not supported** by this manual's RSView import path.
3. Stop the live source and open the saved PCAP. Compare a fixed target and frame orientation with the live result. Inspect the spreadsheet/table view for actual coordinates, range and intensity rather than rely only on point color.
4. Export the selected points to CSV for numeric analysis. The reviewed M1P manual’s export workflow includes calibrated tabular/CSV data; a newer Viewer LAS feature must be established by that actual installed release, not inferred from an Airy manual. Preserve the raw PCAP because exported XYZ cannot reconstruct missing protocol flags or factory status.
5. Use Viewer’s measurement/display tools to compare a known stationary separation and alternate XYZ/range/elevation/azimuth coloring. Treat a visual measurement as a diagnostic, not a certified range-accuracy test.

**Expected result:** replay reproduces the same static geometry and the export contains the selected measurements with a saved coordinate/time interpretation. If packets replay but geometry differs, compare decoder revision, calibration and return mode before changing hardware. [Model-specific RSView and raw-data workflows](https://cdn.robosense.cn/20240322145019_37549.pdf).

### M1P byte offsets and an original geometry fixture

For the manual-matched non-jumbo measurement profile, the header offsets are **0/4 bytes magic; 4/2 packet sequence; 6/2 protocol; 8/1 return; 9/1 time mode; 10/10 timestamp; 20/10 reserved; 30/1 type 0x10; 31/1 MEMS temperature**. Blocks begin at byte **32**, each **47 bytes**, with time offset at block byte 0 and return sequence at 1. Channel n (zero-based 0–4) starts at block byte **2+9n**; range/elevation/azimuth/intensity are at channel bytes **0/2/4/6**, followed by two reserved bytes. DIFOP's published table lists reserved bytes through byte254 while declaring 256 total; retain the final unexplained byte rather than assign it a field.

This original offline fixture exercises the unusual angle encoding without opening a socket or importing a vendor example. It encodes a hypothetical **7.5 m** point at **0° elevation / 90° azimuth**; it is not a captured sensor measurement:

```python
import math
import struct

fixture = struct.pack(
    ">HHHB2x", 1500, 32768, 32768 + 9000, 64)
r_raw, e_raw, a_raw, intensity = struct.unpack(
    ">HHHB2x", fixture)
radius = r_raw * 0.005
elevation = math.radians((e_raw - 32768) * 0.01)
azimuth = math.radians((a_raw - 32768) * 0.01)
xyz = (radius * math.cos(elevation) * math.cos(azimuth),
       radius * math.cos(elevation) * math.sin(azimuth),
       radius * math.sin(elevation))
assert len(fixture) == 9
assert all(math.isclose(a, b, abs_tol=1e-12)
           for a, b in zip(xyz, (0.0, 7.5, 0.0)))
print("XYZ meters:", tuple(round(v, 6) for v in xyz),
      "intensity:", intensity)
```

**Expected result:** `XYZ meters: (0.0, 7.5, 0.0) intensity: 64`. This checks the original arithmetic/fixture only. Production acquisition still needs the matching parser, point times, sequence/return pairing and received status. A missing sequence within a frame suggests reception loss; a reset to1 at the next frame is expected. Retain the return mode because dual output alternates echo packets, and do not interpret initialization/standby/sleep/fault states as an active calibrated scan. [Manual packet/state reference](https://cdn.robosense.cn/20240322145019_37549.pdf).

### M1P complete header offsets

| MSOP header byte offset / size | Reviewed M1P meaning                                                                        |
| ------------------------------ | ------------------------------------------------------------------------------------------- |
| 0/4                            | `55 AA 5A A5` packet identification                                                         |
| 4/2; 6/2                       | Per-frame packet sequence / protocol version                                                |
| 8/1                            | Return flag **0 dual / 4 strongest / 5 last / 6 first**                                     |
| 9/1                            | Time flag **0 internal / 1 PPS reset / 2 PTP / 3 gPTP**, subject to actual firmware support |
| 10/10                          | Six bytes seconds plus four bytes microseconds                                              |
| 20/10                          | Reserved, retain opaque bytes                                                               |
| 30/1; 31/1                     | Device type **0x10**, MEMS temperature **raw−80 °C**                                        |

All multi-byte measurement values use the manual's big-endian encoding. The packet timestamp plus each block's **microsecond `time_offset`** identifies that block's sample time. It is a block offset, not an equal division by the number of channels or the count of received packets. [M1P manual Tables4–7](https://cdn.robosense.cn/20240322145019_37549.pdf).

## Getting started

### First result with RSView <a href="#getting-started-capture-the-first-point-cloud" id="getting-started-capture-the-first-point-cloud"></a>

#### Prerequisites <a href="#prerequisites" id="prerequisites"></a>

Prepare the identified **12 V M1P kit**, its matched automotive-Ethernet interface box, supplied harness/adapter, a wired Gigabit host and an RSView version supporting this packet revision. The sensor's 1000BASE-T1 port is not a direct computer RJ45 port. Read the label and preserve its 9–16 V sensor supply boundary before connecting the kit.

#### Connection, network and RSView <a href="#connection-network-and-rsview" id="connection-network-and-rsview"></a>

1. Record the 12 V unit's model, serial, hardware/firmware and matching kit labels. Wire the powered-off sensor through the supplied automotive-Ethernet interface box as above.
2. Configure the dedicated host adapter to `192.168.1.102/24`; factory sensor address is `192.168.1.200`. Preserve other network interfaces and check for address conflicts. For a previously configured sensor, capture ARP/UDP on the intended interface to learn its actual source/destination instead of setting an all-network mask.
3. Apply approved 12 V-kit power and confirm the wakeup/Normal Run state, not merely an illuminated power indicator. Check link at the interface box and host.
4. Open the compatible RSView build. Choose **File → Open Sensor → RSM1**, as stated for M1P in v1.3.0. Keep the provided sensor configuration; the manual notes that the original stream is already calibrated, so a generic correction file must not introduce a second correction.
5. Confirm 6699 MSOP and 7788 DIFOP if using factory settings. Permit those application/ports on the isolated sensor interface. Inspect a changing cloud against a static target, then record several seconds as **PCAP** and replay it.

**Expected result:** the correct sensor produces a live decoded point cloud and the saved capture reopens with the same geometry. A link LED or received packet alone does not establish correct sensor model, calibration or clock handling. [Manual Appendix A](https://cdn.robosense.cn/20240322145019_37549.pdf).

### Original read-only packet-signature checkpoint

Close RSView/other receiving applications before this standalone test so they do not compete for UDP 6699. Save as `m1p_header_check.py` and run with Python 3 on the configured host. This program does not transmit commands or decode the full point cloud:

```python
import socket
import struct
import time

good = 0
unexpected = 0
first_sequence = None
last_sequence = None
deadline = time.monotonic() + 8.0
with socket.socket(socket.AF_INET, socket.SOCK_DGRAM) as receiver:
    receiver.bind(("0.0.0.0", 6699))
    receiver.settimeout(0.25)
    while time.monotonic() < deadline:
        try:
            payload, peer = receiver.recvfrom(65535)
        except socket.timeout:
            continue
        if len(payload) != 1210 or payload[:4] != bytes.fromhex("55 aa 5a a5"):
            unexpected += 1
            continue
        sequence = struct.unpack_from(">H", payload, 4)[0]
        if first_sequence is None:
            first_sequence = sequence
            print("source", peer[0], "protocol", payload[6:8].hex(),
                  "return_mode", payload[8], "time_mode", payload[9])
        last_sequence = sequence
        good += 1
print("matching", good, "unexpected", unexpected,
      "first_sequence", first_sequence, "last_sequence", last_sequence)
if not good:
    raise SystemExit("No matching M1P-v1.3.0 MSOP observed; inspect link/profile")
```

**Expected result:** matching payloads from the observed sensor and sensible protocol/return/time mode bytes. Sequence numbers cycle with frames; first-to-last subtraction is **not** a loss counter. Timing is host-side and the eight-second receive window is approximate. A different packet size/header calls for the delivered firmware protocol, not a forced decoder selection. [Manual §2.1](https://cdn.robosense.cn/20240322145019_37549.pdf).

### ROS2 decoding and finite capture replay

Prerequisites: documented Ubuntu 22.04/Humble desktop, compiler/colcon, PCL, yaml-cpp/libpcap development packages, and the successful Viewer/packet checkpoint. Use a fresh workspace:

```bash
mkdir -p ~/m1p_ws/src
cd ~/m1p_ws/src
git clone https://github.com/RoboSense-LiDAR/rslidar_sdk.git
cd rslidar_sdk
git checkout 8b4b4b7ff910799260347821084c59e1c73d50d5
git submodule update --init --recursive
cd ~/m1p_ws/src
git clone https://github.com/RoboSense-LiDAR/rslidar_msg.git
source /opt/ros/humble/setup.bash
cd ~/m1p_ws
colcon build
source install/setup.bash
```

Edit `src/rslidar_sdk/config/config.yaml`: live `msg_source:1`,`send_point_cloud_ros:true`,`lidar_type:RSM1`, ports 6699/7788 and output `/rslidar_points`, frame `rslidar`. Run `ros2 launch rslidar_sdk start.py`. In a second sourced terminal inspect `ros2 topic info /rslidar_points --verbose` and `ros2 topic hz /rslidar_points`; use the emitted frame in RViz. [Actual configuration](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/config/config.yaml), [live workflow](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/doc/howto/06_how_to_decode_online_lidar.md).

**Expected result:** current PointCloud2 frames with stable static geometry and advancing timestamps. The source-backed baseline is approximately 10 Hz; confirm actual delivered configuration before interpreting a different rate as a fault.

For an offline finite pass, stop the live driver, set `msg_source:3`, point `pcap_path` at the recorded file and set `pcap_repeat:false`. Keep the same packet model/ports. Compare replay and live geometry before adding a downstream algorithm. If per-point time is needed, select the supported XYZIRT point type in the project's CMake configuration and rebuild; the default XYZI representation is not equivalent. [Replay](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/doc/howto/08_how_to_decode_pcap_file.md), [point types](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/doc/howto/05_how_to_change_point_type.md).

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

| Symptom                                | Ordered checks                                                                                                                                |
| -------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| Power but no packets                   | 12 V variant and 9–16 V supply at sensor, approved wakeup path/Normal Run, 1000BASE-T1 conversion, then RJ45/link                             |
| Host link exists but no sensor traffic | Interface-box state and exact automotive cable; ordinary Ethernet link is not proof of a working T1 sensor link                               |
| MSOP arrives but cloud fails           | 1210-byte/header/firmware match, RSM1 selection, actual 6699/7788, calibration policy and viewer compatibility                                |
| Capture loads incorrectly              | PCAP versus PCAPNG, selected sensor profile, correct ports and enough accompanying DIFOP packets                                              |
| Uneven density / frame seams           | Return/ROI scan pattern, packet sequence/frame handling and host packet loss; MEMS does not have a spinning sensor's ring/azimuth assumptions |
| Timestamp is not UTC                   | Actual gPTP lock status, master clock/transport, hardware timestamp capability and holdover after master loss                                 |
| Thermal or intermittent reset          | Power transient/current margin, cable drop, interface connections and thermal path;15 W is a steady test condition                            |
| Numbers differ from 2022 guide         | Delivered revision/current specification; keep new point rates/weight separate from old protocol/electrical defaults                          |

Recover first by preserving a PCAP/configuration record, closing the receiving application and restarting the exact matched interface/sensor after electrical checks. Do not change a wakeup pin or flash firmware as a network-discovery experiment. Firmware and 24 V hardware require their own exact manufacturer instructions. Clean/protect the optical window and connector using the matching manual; do not open the sensor enclosure. [OEM guide](https://cdn.robosense.cn/20240322145019_37549.pdf).

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

| Resource                                                                                                                                                        | Exact use                                                                                                         |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| [OEM M1P v1.3.0 manual](https://cdn.robosense.cn/20240322145019_37549.pdf)                                                                                      | Downloaded 38-page PDF;12 V electrical/wakeup/TE pinout, packet definitions, RSView, time and mechanical drawings |
| [Official M1 Plus downloads](https://www.robosense.ai/en/resources-11)                                                                                          | Current guide, brochure and RSView access; request form can apply                                                 |
| [Pinned SDK](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/README.md)                                            | ROS/ROS2 build, live and recorded-data workflow                                                                   |
| [Pinned RSM1 decoder](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/driver/decoder/decoder_RSM1.hpp) | Concrete 1210/256-byte layout and format selection                                                                |

Appendix C's connector face and wakeup state diagram were visually inspected. Existing certification attachment is retained; certification material does not replace the electrical manual. The formerly linked distributor PDF may reject downloads; the OEM CDN copy above was read directly.

### Original document attachments <a href="#existing-openelab-file-attachment" id="existing-openelab-file-attachment"></a>

{% file src="../../.gitbook/assets/M1P_Certification.zip" %}

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

Reviewed **24 November 2026**: exact 12 V combined-kit/BOM, current OEM-hosted v1.3.0 manual, connector/state diagrams and pinned SDK/decoder code. Current sales-performance differences are called out rather than silently combined. The bounded packet checker is original.

**RSView/ROS execution, compilation, firmware upgrade, voltage/wakeup tests, gPTP measurements and physical sensing tests: not run.** The walkthrough and expected outputs are source-backed procedures, not observed bench results.

* [RS-LiDAR-M1P OEM User Guide](https://cdn.robosense.cn/20240322145019_37549.pdf) — v1.3.0,2022-12-21; OEM CDN download read 24 Nov 2026.
* [RoboSense ROS2 SDK build workflow](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/README.md) — commit 8b4b4b7ff910799260347821084c59e1c73d50d5.
* [RSM1 decoder packet layout matching M1P manual](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/driver/decoder/decoder_RSM1.hpp) — commit 897b14d3bdb6186a75df27ba51b65b5bd5557723.
* [RSM1 live/PCAP config and ROS fields](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/config/config.yaml) — commit 8b4b4b7ff910799260347821084c59e1c73d50d5.
* [ROS2 live decode procedure](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/doc/howto/06_how_to_decode_online_lidar.md) — commit 8b4b4b7ff910799260347821084c59e1c73d50d5.
* [PCAP replay procedure](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/doc/howto/08_how_to_decode_pcap_file.md) — commit 8b4b4b7ff910799260347821084c59e1c73d50d5.
* [Exact 12 V 3.5 m combined kit/current SKU BOM](https://openelab.io/products/robosense-m1-plus-solid-state-lidar) — 23 Nov catalog; public indexed page observed 24 Nov 2026.

### Additional established references

* [Manufacturer product information](https://store.robosense.ai/products/m1-plus)
* [M1P User Guide, Appendix A](https://cdn.robotshop.com/media/U/UTR/RB-Utr-08/pdf/robosense-rs-lidar-m1-plus-advanced-2d-mems-smart-chip-lidar-200m-range-user-guide.pdf)
* [RS-LiDAR-M1P User Guide, revision 1.3.0 (PDF)](https://cdn.robotshop.com/media/U/UTR/RB-Utr-08/pdf/robosense-rs-lidar-m1-plus-advanced-2d-mems-smart-chip-lidar-200m-range-user-guide.pdf)
* [RoboSense M1 Plus product listing](https://store.robosense.ai/products/m1-plus)
* [RS-LiDAR-M1P User Guide (PDF)](https://cdn.robotshop.com/media/U/UTR/RB-Utr-08/pdf/robosense-rs-lidar-m1-plus-advanced-2d-mems-smart-chip-lidar-200m-range-user-guide.pdf)
* [RoboSense manufacturer M1 Plus listing](https://store.robosense.ai/products/m1-plus)
* [RoboSense RS-LiDAR-M1P User Guide, v1.3.0](https://cdn.robotshop.com/media/U/UTR/RB-Utr-08/pdf/robosense-rs-lidar-m1-plus-advanced-2d-mems-smart-chip-lidar-200m-range-user-guide.pdf)

### Supporting resource links

* [RoboSense rsdriver](https://github.com/RoboSense-LiDAR/rs_driver)
* [RoboSense rslidarsdk](https://github.com/RoboSense-LiDAR/rslidar_sdk)
