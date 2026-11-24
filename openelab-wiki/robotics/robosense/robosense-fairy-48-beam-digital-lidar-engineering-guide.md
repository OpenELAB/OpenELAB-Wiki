---
description: >-
  Identify Fairy48 TX versus 48 T 1, connect the correct harness and physical
  layer, and acquire calibrated 48-channel clouds with RSFAIRY and ROS2 Humble.
---

# RoboSense Fairy 48 Beam Digital LiDAR Engineering Guide

{% hint style="info" %}
[**View RoboSense Fairy 48-Beam Mid-Range Digital LiDAR with 360° × 32° FOV on OpenELAB**](https://openelab.io/products/robosense-fairy-mid-range-lidar?variant=45646246215878)

**Model / option:** Only LiDAR · **SKU:** `RS-Fairy48`
{% endhint %}

## Product overview

### Overview <a href="#overview" id="overview"></a>

**RoboSense Fairy48 is a 48-channel, 360° × 32° LiDAR for medium-range 3D perception.** The assigned `RS-Fairy48` option is **Only LiDAR**. `RS-Fairy48-Accessory` contains accessories without a sensor; `RS-Fairy48-Kit` combines the sensor and accessory package. Neither accessory SKU is counted as an assigned row here. [Exact store options](https://openelab.io/products/robosense-fairy-mid-range-lidar).

The manufacturer publishes separate **48 TX** and **48T1** manuals. The store's sensor SKU does not encode the physical Ethernet type: inspect the delivered label and matched cable/interface box before connection. This guide provides both documented paths explicitly. Do not infer conventional Ethernet from an aviation connector or a generic “Ethernet” description. [48 TX manual](https://robosense-robotics.github.io/product-manual/en/Fairy_48TX/), [48T1 manual](https://robosense-robotics.github.io/product-manual/en/Fairy_48T1/).

### Product And Variant Information <a href="#product-and-variant-information" id="product-and-variant-information"></a>

`RS-Fairy48` is the sensor-only option. The accessory-only and sensor-plus-accessory options are separate packages, and none of those SKU names proves whether the supplied sensor is 48TX or 48T1. The physical-layer mapping and unavailable connector-face drawing remain named unresolved gaps; the two reference harnesses even reverse the power-branch contact order.

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/Fairy_48TX/).

## Applications

Fairy48 supports mobile-robot mapping, mid-range scene capture and 3D obstacle-contour development. Its symmetric vertical envelope, −15.84° to +15.84°, differs from the upward-facing Airy family. Select mounting height and pitch using actual channel angles, then check representative low and overhead obstacles rather than assuming every object inside a volume receives a return.

The manual describes about 6 ms of unavailable cloud data per second, appearing as an approximately 30° gap in one of every ten frames. Its start angle is configurable. Compare single frames, accumulated stationary data and packet counts before declaring a network fault. On a moving carrier, accumulation also requires per-point timing and motion compensation. [FOV and frame-start setting](https://robosense-robotics.github.io/product-manual/en/Fairy_48TX/).

### Project References And Application Ideas <a href="#project-references-and-application-ideas" id="project-references-and-application-ideas"></a>

* 360-degree mapping and obstacle detection for robots.
* Mid-range point-cloud datasets for perception algorithms.
* Web UI and RSView-based sensor validation workflows.
* ROS/ROS 2 point-cloud integration with fixed-IP UDP LiDAR data.
* Return-mode comparison for vegetation, reflective targets, or multi-surface scenes.

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/Fairy_48TX/).

## Specifications <a href="#specifications" id="specifications"></a>

| Parameter             | Fairy48, manual v1.0 /2026-02-01                             |
| --------------------- | ------------------------------------------------------------ |
| Channels / field      | 48; 360° horizontal;−15.84° to +15.84° vertical              |
| Range                 | 150 m maximum;80 m at 10% NIST reflectance                   |
| Blind zone            | ≤0.2 m                                                       |
| Angular sampling      | 0.25° horizontal; about 0.67° vertical                       |
| Rotation / frame rate | 600 RPM /10 Hz                                               |
| Typical precision     | 0.5 cm,1σ; repeatability, not complete mapping accuracy      |
| Point output          | About 690,000/s single;1,380,000/s dual return               |
| Return choices        | Strongest, first, last, dual                                 |
| Supply / consumption  | 9–32 V DC;<10 W, environment dependent                       |
| Body / mass           | Φ75 × H 70 mm;<350 g sensor without cable                    |
| Temperature           | −40 to +60 °C operating;−40 to +85 °C storage                |
| Protection            | IP67 /IP6K9K sensor; complete harness protection is separate |
| Timing / motion       | GPS, PTP, gPTP; integrated IMU                               |

[Both official 48-line specification tables](https://robosense-robotics.github.io/product-manual/en/Fairy_48TX/), [T1 counterpart](https://robosense-robotics.github.io/product-manual/en/Fairy_48T1/). The manual also lists Ethernet bandwidth below 19 Mbps alongside single/dual rates without fully separating those conditions. Do not size a dual-return multi-sensor network solely from that number; measure the selected mode's actual traffic and retain headroom. The 96-channel Fairy's rates are not applicable to this SKU.

## Hardware and connections

### Select the physical-layer branch before wiring <a href="#wiring-and-interface" id="wiring-and-interface"></a>

| Feature               | Fairy48 TX                                        | Fairy48T1                                                                      |
| --------------------- | ------------------------------------------------- | ------------------------------------------------------------------------------ |
| Sensor link           | 100BASE-TX, separate RX/TX pairs                  | 100BASE-T1, single differential pair                                           |
| Sensor pins 1/2       | RX+ /RX−                                          | NA; do not connect as an RX pair                                               |
| Pins 3/4              | TX+ /TX−                                          | T1 differential link, labeled 1P/1N in its manual                              |
| Host connection       | Matched TX breakout to conventional Ethernet      | Matched T1 cable and compatible interface box/media converter to host Ethernet |
| Power-harness mapping | TX reference branch: positive pin 1, ground pin 2 | T1 reference branch: ground pin 1, positive pin 2                              |

**The power-branch contact order differs between the two reference harnesses.** Use the exact assembly's labels/table, not an Airy cable or the other Fairy drawing. A passive adapter does not convert T1 to TX. [TX interface table](https://robosense-robotics.github.io/product-manual/en/Fairy_48TX/#33-interface-description), [T1 table and adapter box](https://robosense-robotics.github.io/product-manual/en/Fairy_48T1/#33-interface-description).

The common sensor-side contacts are **5/8 GND,6/7 VIN,9 GPS\_PPS,10 SYNC\_OUT1,11 GPS\_GPRMC**. PPS accepts 3.0–15.0 V positive pulses; GPRMC uses RS232. These are not the Airy Lite 3.3 V-only PPS limits. Leave both sync inputs and the output unconnected/insulated for first capture. Do not connect two outputs together. For GPS, follow the documented 9600 baud 8N1 and PPS/message timing; for PTP/gPTP, match master profile, transport/domain and verify lock.

The official online connector drawings are hosted on an external image CDN that returned Access Denied during review. The electrical tables are readable, but this guide intentionally uses **intact manufacturer-matched harnesses** and supplies no custom face-numbering construction procedure. Obtain the delivered assembly drawing before fabricating a cable.

### Mechanical installation

Use three M4 screws with 3.5–4.5 mm engagement beyond the mounting surface and 15±1 kgf·cm torque, plus the specified Φ3 mm locating pins protruding no more than 3 mm. Check the delivered structural drawing before machining: the online text's mounting-flatness unit is malformed, so it is not reproduced as a fabrication tolerance. Allow ≥5 × cable diameter bend radius for the 6±0.2 mm cable, slack and strain relief. Avoid clamping the housing between top/bottom surfaces.

Provide a conductive bracket and airflow; the manual recommends bracket conductivity>50 W/(m·K). Keep the optical cover free of load and avoid obstructing the scan. Measure the base-frame transform after final mounting. Use actual DIFOP angle and IMU calibration rather than a nominal evenly spaced 48-line model. [Installation and calibration appendices](https://robosense-robotics.github.io/product-manual/en/Fairy_48TX/).

### Manufacturer drawings and retained diagrams

![RoboSense Fairy product image](<../../.gitbook/assets/robosense fairy product.jpg>)

_Manufacturer drawings retained from this guide. Use the stated model/revision and the original manual when interpreting connector views and dimensions._

### Hardware Architecture <a href="#hardware-architecture" id="hardware-architecture"></a>

Fairy combines a rotating 48-line LiDAR, internal processing and IMU. Sensor Ethernet is either conventional 100BASE-TX with separate pairs or automotive 100BASE-T1 with one differential pair. A matched T1 media-conversion box performs active physical-layer conversion; a passive aviation-to-RJ45 adapter does not. Housing shape and the common 11-pin family connector do not identify that branch.

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/Fairy_48TX/).

## Software and development resources

### Default Network Settings <a href="#default-network-settings" id="default-network-settings"></a>

The reviewed RoboSense SDK supports `RSFAIRY`. Its decoder recognizes **48-channel model byte 0x01** and **96-channel byte 0x02**, with different firing timing. The generic 96-channel allocation in the source is not evidence that this product has 96 channels. Preserve actual packet model identification and use the exact decoder. [Decoder](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/driver/decoder/decoder_RSFAIRY.hpp).

| Stream / setting         | Fairy48 baseline                                                  |
| ------------------------ | ----------------------------------------------------------------- |
| Sensor / host target     | 192.168.1.200 /192.168.1.102                                      |
| Cloud MSOP               | UDP 6699,1248-byte payload, magic `55 aa 05 5a`                   |
| Calibration/status DIFOP | UDP 7788,1248-byte payload, magic `a5 ff 00 5a 11 11 55 55`       |
| IMU                      | Enabled/configured separately;51-byte packet supported by decoder |
| SDK live/replay          | `msg_source:1` live;`3` PCAP                                      |
| Exact model              | `lidar_type:RSFAIRY`                                              |
| Default ROS output       | `/rslidar_points`, frame `rslidar`                                |

[Manual protocol/default network](https://robosense-robotics.github.io/product-manual/en/Fairy_48TX/), [SDK configuration](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/config/config.yaml). The actual decoder masks a range feature bit; do not treat every raw distance bit as range. It uses different block iterators for the 48-channel/return layout. A hand-written generic polar decoder can produce plausible but wrong geometry.

RSView handles live display, PCAP replay, table views and export. Use a supporting Fairy profile/build. PCAPNG is not accepted by the manual's replay workflow. For ROS2, use the documented Ubuntu 22.04/Humble target, PCL, yaml-cpp, libpcap and official `rslidar_msg`. For ring/time, edit CMake's direct `POINT_TYPE` assignment to `XYZIRT`; IMU additionally needs its compile option and actual configured port. [SDK build](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/README.md).

### Field Of View And Return Modes <a href="#field-of-view-and-return-modes" id="field-of-view-and-return-modes"></a>

The exact 48-line manuals define −15.84° to +15.84° vertical angles and distinguish strongest, first, last and dual return. Their scanning sequence produces about **6 ms without points per second**, reported as a roughly **30° gap in one of every ten frames**; the gap's start angle is configurable. That periodic, located gap is different from random packet-loss holes. Keep the configured start angle and return mode with a PCAP, and compare a repeated pattern before calling it a failed channel.

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/Fairy_48TX/).

### Communication Protocol <a href="#communication-protocol" id="communication-protocol"></a>

The RSFAIRY decoder selects its block iterator and firing-time table from the channel/return layout. Its 48-line model byte is 0x01; the source's 96-line branch is 0x02 and must not supply this sensor's geometry. Preserve the 1248-byte MSOP cloud packets and DIFOP calibration/status packets together. IMU is a separate 51-byte output and needs its own configured receiver/parse option.

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/Fairy_48TX/).

### SDK configuration, recording and replay behavior

The pinned SDK uses one shared `common` block and one `lidar` list entry per sensor. For **Fairy48**, keep **`lidar_type:RSFAIRY`** and the model-specific network/packet revision above. The receive-port baseline is **6699/7788/6688 after resolving the physical-layer branch**; these are not permission to transfer a cable, wake signal or decoder from a similar model.

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

### Fairy48 status fields and protocol revision boundaries

The read-only DIFOP packet is also the useful record of **what was configured**, beyond a point cloud. In both 48-line manuals, relevant fields include network addresses at **10/14**, MAC at **18**, MSOP/DIFOP ports **24/28**, firmware fields **40/45/50/55**, serial **292**, return mode **300**, sync mode/state **301/302** and seconds/microseconds time **303**. PTP profile/domain parameters begin at **85/87**; GPS status at **357** separates PPS/GPRMC/UTC locks from mere input presence. These offsets are bytes from the DIFOP start, not Ethernet-frame offsets.

IMU configuration at **358–363** records enable, actual UDP port, rate and accelerometer/gyro ranges. The listed rate codes 0–3 are **25/50/100/200 Hz**. Real-time phase/speed are at **371/373**; angle arrays at **468/756** use a sign byte and two-byte 0.01° magnitude per entry. The 288-byte arrays reserve 96 entries in this packet family; they do not prove the sold sensor has 96 channels. Device/mainboard/baseboard voltage fields at **1066/1044/1068** use raw/100 V, while **1092/28 bytes** carries the IMU-to-LiDAR quaternion/translation. [48TX status/calibration tables](https://robosense-robotics.github.io/product-manual/en/Fairy_48TX/), [48T1 counterpart](https://robosense-robotics.github.io/product-manual/en/Fairy_48T1/).

The measurement packet uses eight 148-byte blocks after a 42-byte header and a tail/reserved region totaling 22 bytes. Each block has `FF EE`, 0.01° azimuth and 48 range/reflectivity entries. Range is **`raw & 0x7FFF` × 0.005 m**. Return pairing and firing time depend on the actual 48-channel mode and decoder iterator; do not reuse Airy's upper-two-bit mask or 96-channel ordering. The manual's header table prints model byte `0x02` beside a 48-beam label, but the pinned decoder selects **`0x01` for 48 / `0x02` for 96**. Its timestamp table also says nanoseconds where the accompanying note/appendix and decoder use microseconds. Those source inconsistencies are reasons to retain the actual firmware/PCAP and use the exact decoder, rather than build a parser from a mislabeled table. [Pinned Fairy decoder and model selection](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/driver/decoder/decoder_RSFAIRY.hpp).

The web interface's phase-lock angle, frame-start blanking angle and angle-pulse output are different controls. A frame boundary only groups host points; phase lock aligns rotor phase across sensors; an output pulse is an electrical timing signal. Save these values with return/time/network settings before changing them. The additional protocol detail does not resolve the sold TX/T1 branch or connector-face drawing gap: use only the identified complete assembly and leave custom harness construction bounded.

### Native driver API and callback backpressure

A native C++ integration uses the pinned `LidarDriver<PointCloud>` API: register the free-cloud/completed-cloud callbacks and exception callback, populate `RSDriverParam` with this model's decoder/input settings, check `init()` and `start()` Boolean results, then call `stop()` to join the acquisition threads. `regPacketCallback` exposes packets separately from decoded clouds, while `getTemperature`, `getDeviceInfo` and `getDeviceStatus` return a Boolean indicating whether the requested information is available. A valid API method does not mean every model populates every field. [Public native API](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/api/lidar_driver.hpp).

The user's callbacks execute on the driver's decoding thread. Queue the completed cloud for a separate processing thread and recycle buffers after consumption; avoid mapping, file compression or slow network calls inside the callback. The documented consequence of blocking is **`ERRCODE_PKTBUFOVERFLOW` and discarded packets**, which can resemble a bad Ethernet link. Separate link/capture loss from application backlog before changing the sensor's power or calibration. Native `decodePacket` can consume an externally supplied packet source, but still needs the correct model framing and calibration. libpcap is needed for native PCAP input, Eigen for internal transforms, and PCL/Boost for the optional visualization tool; they are not all intrinsic requirements of every receive-only application. [Thread ownership and buffer queues](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/doc/intro/03_thread_model.md), [native dependencies and demo build options](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/README.md).

### Web controls, synchronization thresholds and upgrade verification

Use the delivered **Fairy48** firmware's web interface on the isolated sensor network. Record the current page/settings first. The manual's **General Setting**, **Performance Setting**, **Angle Pulse Setting**, **Diagnostic** and **System** pages perform different roles; the following values are the reviewed manual profile, not a universal future firmware default.

| Control group            | Documented inputs and behavior                                                                                                                                             |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Network                  | Device and target on the same subnet; default unicast target `.102`; `255.255.255.255` is broadcast. MSOP/DIFOP ports **1025–65535**, and they must differ                 |
| Return / operation       | Select the exact supported return mode above; High Performance is default, Standby stops motor and transmitter                                                             |
| Time source              | GPS, PTP E2E-L4, P2P, gPTP or E2E-L2; match master transport/profile/domain                                                                                                |
| PTP domain / peer delay  | Domain **0–127**; Respond To PeerDelayRequest off by default; do not change it without the intended network role                                                           |
| Leap-second option       | No Leap Second off by default; retain the clock source's expected timescale                                                                                                |
| Master loss              | Timeout **1–255 s**, default **5 s**, before leaving synchronized state                                                                                                    |
| Lock / unlock hysteresis | Both thresholds **1–255 ms**; lock default **1 ms**, unlock **20 ms**. A locked icon is not a sub-microsecond accuracy claim                                               |
| Phase lock               | Rotor reference angle **0–360°**, distinct from where the host splits a frame                                                                                              |
| IMU                      | Control on by default; actual port **1025–65535**; output **25/50/100/200 Hz**, default 200 Hz; ±2/4/8/16 g and ±250/500/1000/2000 degrees/s, defaults ±4 g/±500 degrees/s |
| Performance              | Reflectivity Enhancement off by default; Trail Filter **1–7, default 4**; frame-start/gap angle **0–360°**                                                                 |

Fairy48 has its own **frame-start blanking angle 0–360°** and trailing-filter levels. Do not transfer Airy’s optional channel or gap-fill switches to Fairy merely because both use the same style of web UI.

Angle Pulse uses **SYNC OUT1**, an enable switch, integer start angle, pulse width and a step entered to one decimal place. **Mode 1 increases the first pulse width by 25%; Mode 2 does not**; this manual defaults to **Mode 2**. The pulse-output setup is not a GPS input setting or proof of PTP lock. The manual does not establish a universal safe electrical load/range for an arbitrary attached receiver, so retain the model-specific signal limits and do not connect a guessed trigger circuit. Click **Save** and require the successful response, then reread settings; a typed value alone is not confirmed applied. [Exact manual Appendix A2](https://robosense-robotics.github.io/product-manual/en/Fairy_48TX/#a2-product-parameter-setting).

The Diagnostic page refreshes about every **5 s** and exposes voltage/current, device temperature, RPM, rotor phase, laser on/off, PPS/GPRMC state, sync mode/time/Lock, startup count and accumulated running time. Red voltage/current should first be interpreted against Standby versus active state. Check a readback, then correlate with the packet status/capture; do not mistake the slow page refresh for a missing 10 Hz cloud. [Diagnostic page](https://robosense-robotics.github.io/product-manual/en/Fairy_48TX/#a3-product-diagnosticsoperational-status).

Firmware recovery is component-specific. Obtain a package for the exact model, board revision and serial; preserve settings/calibration and establish stable power first. In **System**, choose the supplied **ZIP**, verify the shown filename and select its matching application/mainboard/baseboard action. The manual names component payloads `.hs_fs`, `.bin` and `.bit` respectively; these internal suffixes are not instructions to upload an unrelated raw file or repackage firmware. The public instructions do not establish a mandatory cross-component flashing order or an emergency bootloader procedure. After the supported operation, reread each affected version and recheck cloud/calibration/time; on failure save the error and use manufacturer-directed recovery rather than repeat another board's image. [Official upgrade requirements](https://robosense-robotics.github.io/product-manual/en/Fairy_48TX/#a4-product-firmware-upgrade).

### Fairy48 IMU fields and complete firing-delay groups

The Fairy 51-byte IMU profile begins **`AA 55 5A 05`**, followed by the 10-byte seconds/microseconds timestamp at **4**. Its acceleration XYZ at **14/18/22** is float32 **m/s²**; gyro XYZ at **26/30/34** is float32 **rad/s**. Signed temperature at **38** uses 0.01 °C, selector bytes are at **42/43/44**, uint32 sequence at **45**, and `F0 0F` tail at **49**. Unlike Airy96, these axes are already physical floats in the reviewed Fairy protocol/decoder; do not multiply them by an Airy raw-count scale.

The manual lists ODR selector **0/1/2/3/4 = 25/50/100/200/1000 Hz**, accelerometer selector **0/1/2/3 = ±2/4/8/16 g**, and gyro selector **0/1/2/3 = ±250/500/1000/2000 degrees/s**. The web interface only lists output rates through 200 Hz and the pinned decoder reserves the three selector bytes; it does not rescale the float axes with them. Record the actual firmware/output setting rather than infer that a listed enum is a universally enabled UI control.

| Zero-based Fairy48 channel indices | Transmission delay |
| ---------------------------------- | ------------------ |
| 00–07                              | 0 ns               |
| 08–15                              | 5,280 ns           |
| 16–23                              | 14,080 ns          |
| 24–31                              | 28,160 ns          |
| 32–39                              | 42,240 ns          |
| 40–47                              | 51,040 ns          |

Appendix E's delays attach to the appropriate channel within the correct return/block timing sequence. The 48-channel single/dual paths use different iterators; do not add a channel delay again after consuming a point already timestamped by the official decoder. Retain the IMU-to-LiDAR quaternion/translation and measure LiDAR-to-robot extrinsics as separate transforms. [Exact48 manual IMU/Appendices C/E](https://robosense-robotics.github.io/product-manual/en/Fairy_48TX/), [matching decoder time and IMU implementation](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/driver/decoder/decoder_RSFAIRY.hpp).

The real-time-RPM appendix gives **0x0128 as 600**, although the big-endian integer is **296**; preserve the raw field and compare against the diagnostic page rather than invent a conversion factor from that erroneous example. The general 0.1 RPM scale in AiryLite is not established by this Fairy example. [Fairy Appendix C9](https://robosense-robotics.github.io/product-manual/en/Fairy_48TX/).

## Getting started

### First cloud using the verified hardware branch <a href="#software-and-setup-workflow" id="software-and-setup-workflow"></a>

1. Identify **48 TX or 48T1** on the received device/assembly. Confirm sensor-only versus kit contents and obtain the matching cable, power path and, for T1, interface box. If the type cannot be identified, stop before electrical connection.
2. Mount securely and connect with power off. Use a matched approved supply within 9–32 V at the sensor; the manual's evaluation accessory adapter is 12 V 3.34 A/40 W. Do not apply its rating to an unrelated accessory.
3. Configure the dedicated host adapter to **192.168.1.102/24**. Connect TX directly through its breakout, or T1 through its documented converter. Energize the approved assembly and confirm Ethernet link.
4. Open `http://192.168.1.200` on that isolated network. Record model, serial, board/app/motor firmware, voltage, RPM, return mode, time mode and network destinations. Read first; do not reset unknown settings.
5. Start a supporting RSView build with the Fairy profile. Receive 6699/7788, observe a stationary diffuse target, record a short PCAP and replay it. Compare individual frames with the documented gap behavior.

**Expected result:** the correct Fairy48 identity and calibrated scene are visible, and the recording replays with coherent geometry. This procedure depends on identifying the delivered physical layer; matching UDP ports does not resolve it. [Both quick-connection chapters](https://robosense-robotics.github.io/product-manual/en/Fairy_48TX/), [T1 path](https://robosense-robotics.github.io/product-manual/en/Fairy_48T1/).

### Original read-only status snapshot

Close other clients first. Run this Python 3 receiver on the configured host. It listens eight seconds on DIFOP 7788 and sends no configuration command:

```python
import ipaddress
import socket
import time

prefix = bytes.fromhex("a5 ff 00 5a 11 11 55 55")
received = 0
with socket.socket(socket.AF_INET, socket.SOCK_DGRAM) as sock:
    sock.bind(("192.168.1.102", 7788))
    sock.settimeout(0.2)
    end = time.monotonic() + 8
    while time.monotonic() < end:
        try:
            data, peer = sock.recvfrom(65535)
        except socket.timeout:
            continue
        if len(data) != 1248 or not data.startswith(prefix):
            print("unexpected", peer, len(data), data[:8].hex())
            continue
        received += 1
        if received == 1:
            print("sensor", str(ipaddress.IPv4Address(data[10:14])))
            print("target", str(ipaddress.IPv4Address(data[14:18])))
            print("MSOP port", int.from_bytes(data[24:26], "big"),
                  "DIFOP port", int.from_bytes(data[28:30], "big"))
            print("return flag", hex(data[300]), "time mode", data[301],
                  "time status", data[302])
print("valid DIFOP received", received)
if not received:
    raise SystemExit("No DIFOP; inspect actual host destination, interface and port")
```

**Expected result:** the reported endpoints match the device settings, and return flag 0/1/2/3 corresponds to strongest/first/last/dual. A status byte is not by itself a decoded proof of UTC; interpret the exact manual's time-state table. This is a packet/status check, not a cloud-calibration test. [DIFOP layout](https://robosense-robotics.github.io/product-manual/en/Fairy_48TX/).

### ROS2 Humble publisher

After the GUI/capture checkpoint, use a fresh workspace:

```bash
mkdir -p ~/fairy48_ws/src
cd ~/fairy48_ws/src
git clone https://github.com/RoboSense-LiDAR/rslidar_sdk.git
cd rslidar_sdk
git checkout 8b4b4b7ff910799260347821084c59e1c73d50d5
git submodule update --init --recursive
cd ~/fairy48_ws/src
git clone https://github.com/RoboSense-LiDAR/rslidar_msg.git
```

Set `config/config.yaml` to `msg_source:1`,`lidar_type:RSFAIRY`, ports 6699/7788 and `send_point_cloud_ros:true`. Retain DIFOP calibration reception. Choose the actual IMU port from device configuration rather than assuming it from another model. Keep the default point type for the first display, or deliberately select XYZIRT before building if the consumer needs ring/time.

```bash
cd ~/fairy48_ws
source /opt/ros/humble/setup.bash
colcon build --symlink-install
source install/setup.bash
ros2 launch rslidar_sdk start.py
```

In a second sourced terminal, check `ros2 topic hz /rslidar_points` and its header/frame. Set RViz Fixed Frame to `rslidar` unless a verified transform exists. **Expected result:** updating 48-channel calibrated geometry. For replay, set `msg_source:3` and the actual `pcap_path`, keeping the same model and ports. [SDK live/replay instructions](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/README.md).

### Engineering Setup Checklist <a href="#engineering-setup-checklist" id="engineering-setup-checklist"></a>

1. Identify **48TX versus 48T1** from the delivered label and obtain its matched harness/interface drawing; stop if that branch is unresolved.
2. Check the exact power-branch contact order with power disconnected, and leave GPS/timing leads insulated.
3. Record actual IP/ports, firmware and 48-channel model ID, then establish a coherent RSFAIRY cloud using the appropriate physical-layer path.
4. Save DIFOP/calibration and a short static PCAP, and replay it before adding return-mode changes, synchronization or robot motion.

The present SKU does not resolve step 1; this checklist is a bounded reference, not approval to energize an unidentified assembly.

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/Fairy_48TX/).

## Troubleshooting and FAQs

### Troubleshooting <a href="#troubleshooting" id="troubleshooting"></a>

| Symptom               | Useful checks                                                                                    |
| --------------------- | ------------------------------------------------------------------------------------------------ |
| No host Ethernet link | TX versus T1, matching converter and harness; passive connectors do not convert physical layers  |
| Repeated boot         | Sensor-side voltage/cable drop, correct harness power-branch order and supply capability         |
| UDP but wrong cloud   | `RSFAIRY`, packet 48-channel model identification, DIFOP calibration and return layout           |
| Periodic sector gap   | Expected scan architecture; inspect packet counts and frame accumulation before changing network |
| No IMU                | Device enable/rate/port plus compiled parser option; verify actual configuration                 |
| Timing fusion fails   | Clock profile/domain/lock, per-point timing, frame transform and IMU calibration                 |

**Does this guide cover Fairy96?** No. Its decoder shares infrastructure, but the assigned product is 48-channel with its own rates/timing.

**Is a “successful” Save message enough?** It confirms a setting was accepted. Re-read it and verify its observable effect; network changes can remove the device from the current subnet.

The web UI exposes general network/return/time settings, performance filters, frame-start angle, angle-pulse output, diagnostics and firmware upgrade. Change one parameter at a time after saving a known capture. Phase lock, frame splitting and external angle pulses are different mechanisms. Obtain exact firmware through RoboSense; the SDK checkout contains no universal flash image. Clean loose contamination before wiping, protect the cover from scratches and store dry within its limits. [Manual web/maintenance appendices](https://robosense-robotics.github.io/product-manual/en/Fairy_48TX/).

### Best Practices And Limitations <a href="#best-practices-and-limitations" id="best-practices-and-limitations"></a>

* Confirm the final hardware, firmware, and return-mode configuration before production use.
* Account for the documented 30-degree point-cloud gap behavior when planning sensor placement.
* Range, precision, power, and thermal behavior depend on target reflectivity, distance, ambient light, and airflow.
* Use PCAP captures as a regression artifact before writing or changing parsers.
* Do not assume optional time-sync accessories are included; verify the purchased kit.

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/Fairy_48TX/).

### FAQ <a href="#faq" id="faq"></a>

**Can the sensor go straight to a laptop RJ45 port?** Only the verified TX branch uses conventional Ethernet through its matched breakout. The T1 branch needs the correct active converter and harness.

**Is a 30° periodic gap always packet loss?** No: the manual describes its scan-sequence gap. Check whether it repeats at the configured position, then compare received packets and decoder diagnostics.

**Which parts remain unverified?** The exact sold physical layer and connector-face fabrication view. Those limits prevent custom-cable commissioning; they do not justify substituting another Fairy or Airy drawing.

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/Fairy_48TX/).

## Downloads and technical documents

### Resources <a href="#resources" id="resources"></a>

| Resource                                                                                                                                                     | Scope                                                                     |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------- |
| [48 TX manual v1.0](https://robosense-robotics.github.io/product-manual/en/Fairy_48TX/)                                                                      | Conventional Ethernet, pin table, web UI, packets, calibration and timing |
| [48T1 manual v1.0](https://robosense-robotics.github.io/product-manual/en/Fairy_48T1/)                                                                       | Single-pair Ethernet, interface box and different power-branch contacts   |
| [Fairy decoder](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/driver/decoder/decoder_RSFAIRY.hpp) | Actual 48/96 model detection, return layout and IMU support               |
| [ROS SDK](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/README.md)                                            | Supported model/build, live and PCAP examples                             |
| [RoboSense download center](https://www.robosense.ai/en/resources)                                                                                           | Exact viewer, firmware and mechanical/support resources                   |

The existing native Fairy product figure is retained. The online connector-image CDN was inaccessible; use an approved intact harness and obtain its original connector-face drawing before custom wiring.

## References and validation

### Source Notes <a href="#source-notes" id="source-notes"></a>

Reviewed 24 November 2026: both official Fairy48 TX/T1 manuals and appendices, exact sensor-only store option, and actual RSFAIRY model-selection/packet source. The SKU's physical-layer ambiguity is handled with explicit separate branches and an identification checkpoint; no T1-to-TX or harness-polarity substitution is inferred.

**SDK compilation, RSView/ROS execution, status-receiver execution, firmware update and physical electrical/range/timing tests: not run.** The status snapshot is original and syntax checked.

* [Fairy48 TX official manual](https://robosense-robotics.github.io/product-manual/en/Fairy_48TX/) — v1.0 2026-02-01; tables/chapters read; external images blocked.
* [Fairy48T1 official manual](https://robosense-robotics.github.io/product-manual/en/Fairy_48T1/) — v1.0 2026-02-01; tables/chapters read; external images blocked.
* [RoboSense SDK build/model support](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/README.md) — commit 8b4b4b7ff910799260347821084c59e1c73d50d5.
* [Fairy48/96 decoder and model selection](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/driver/decoder/decoder_RSFAIRY.hpp) — commit 897b14d3bdb6186a75df27ba51b65b5bd5557723.
* [Exact Fairy48 sensor-only options](https://openelab.io/products/robosense-fairy-mid-range-lidar) — 23 Nov catalog plus observed public page 24 Nov.
