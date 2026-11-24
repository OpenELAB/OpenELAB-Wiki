---
description: >-
  Wire and commission E1R sensor,3.5 m and 8 m kits through automotive Ethernet,
  verify vector packets and publish ROS2 clouds with the matched RSE1 decoder.
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

# Robosense E1R

{% hint style="info" %}
[**View RoboSense E1R Fully Solid-State LiDAR with 120° × 90° Ultra-Wide FOV for Robotics on OpenELAB**](https://openelab.io/products/robosense-e1r-solid-state-lidar?variant=45547586126022)

**Model / option:** Only LiDAR · **SKU:** `RS-E1R`

[**View RoboSense E1R Fully Solid-State LiDAR with 120° × 90° Ultra-Wide FOV for Robotics on OpenELAB**](https://openelab.io/products/robosense-e1r-solid-state-lidar?variant=45547588812998)

**Model / option:** LiDAR with 3.5 m Ethernet Kit · **SKU:** `RS-E1R-35kit`

[**View RoboSense E1R Fully Solid-State LiDAR with 120° × 90° Ultra-Wide FOV for Robotics on OpenELAB**](https://openelab.io/products/robosense-e1r-solid-state-lidar?variant=45547586158790)

**Model / option:** LiDAR with 8 m Ethernet Kit · **SKU:** `RS-E1R-80kit`
{% endhint %}

## Product overview

### Robosense E1R <a href="#robosense-e1r" id="robosense-e1r"></a>

**RoboSense E1R is a fully solid-state 120° × 90° LiDAR using 1000BASE-T1 automotive Ethernet.** A matched interface box converts the sensor connection to ordinary gigabit RJ45 Ethernet for a computer. It is not a direct-RJ45 Airy and does not share an Airy pinout or decoder.

| Covered SKU    | Exact purchase option                                             |
| -------------- | ----------------------------------------------------------------- |
| `RS-E1R`       | Sensor-only; provide approved power/interface hardware separately |
| `RS-E1R-35kit` | Sensor with 3.5 m Ethernet kit                                    |
| `RS-E1R-80kit` | Sensor with 8 m Ethernet kit                                      |

The two combined kits change harness length and supplied accessories, not the E1R packet format. Their listed set includes the matched power/Ethernet cable, power adapter/cord, interface box, RJ45 cable and fasteners. Confirm the actual labels and contents; accessory-only options do not include a sensor. [Exact store options](https://openelab.io/products/robosense-e1r-solid-state-lidar), [E1R manual](https://robosense-robotics.github.io/product-manual/en/E1R/).

### Product Link <a href="#product-link" id="product-link"></a>

The [E1R listing](https://openelab.io/products/robosense-e1r-solid-state-lidar) has separate sensor-only, 3.5 m combined-kit and 8 m combined-kit options. The latter two change the supplied harness/accessories, not the solid-state sensor's 1200-byte packet format. Verify the delivered harness length and matched interface box before applying the 9–16 V sensor/wakeup requirements.

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/E1R/).

## Applications

### Description <a href="#description" id="description"></a>

Use E1R for wide vertical coverage around a mobile robot, close-range obstacle-perception experiments and three-dimensional mapping. Its forward sector needs deliberate mounting pitch and complementary coverage where a complete robot must observe behind or beside the sensor.

Begin with one stationary planar target and a measured mounting pose. Compare the direction-vector decoded cloud to the actual target before adding time synchronization or motion. The sensor's optical envelope is wider than a simple central-axis line; covers, glass and nearby trim can block useful returns even when the aperture appears clear. [FOV and cover guidance](https://robosense-robotics.github.io/product-manual/en/E1R/#22-optical-envelope-fov-definition).

The factory sensor is a measurement source, not an autonomous obstacle-avoidance controller. System-level performance depends on target reflectivity, illumination, power, calibration, latency and the chosen host pipeline.

## Specifications <a href="#specifications" id="specifications"></a>

| Parameter                 | E1R specification and condition                                                |
| ------------------------- | ------------------------------------------------------------------------------ |
| Principle / wavelength    | Time of flight,940 nm; Class 1 intact-product eye-safety classification        |
| FOV                       | 120° H(±60°) × 90° V(±45°)                                                     |
| Range / near blind zone   | 30 m at 10% NIST under 100 klx direct sunlight /0.1 m                          |
| Average angular sampling  | 0.625° H/V; not uniform guaranteed resolution at every position                |
| Range precision           | ±5 cm at 1σ under manufacturer test conditions                                 |
| Point / frame rate        | About 260,000 points/s /10 Hz                                                  |
| Data link                 | 1000BASE-T1 sensor side, UDP; gigabit-only interface-box RJ45                  |
| Supply / consumption      | 9–16 V DC /<10 W; startup/current margin still required                        |
| Wakeup                    | 9–16 V High in the E1R state-machine description; not a GPIO logic-level input |
| Timing                    | gPTP and PTP-E 2 E L2, matched firmware/profile                                |
| Body / installed envelope | 95 × 42.6 × 69.5 mm body;95 × 51.1 × 87 mm including connector/mount outline   |
| Mass / ingress            | 330±20 g sensor /IP67, IP6K9K conditions                                       |
| Temperature               | −40 to 85 °C operation;−40 to 105 °C storage                                   |

[Current E1R manual §§2.3,3.3](https://robosense-robotics.github.io/product-manual/en/E1R/). Always distinguish the body from the installed envelope when making a wall recess or enclosure.

| Network / protocol   | Factory/reference value                                                                      |
| -------------------- | -------------------------------------------------------------------------------------------- |
| Sensor / target host | 192.168.1.200 /192.168.1.102                                                                 |
| MSOP / DIFOP UDP     | 6699 /7788                                                                                   |
| Payload lengths      | 1200 byte MSOP /256 byte DIFOP                                                               |
| Measurement layout   | 32-byte header,96 × 12-byte vector blocks,16-byte tail                                       |
| Distance / direction | 5 mm per range count; three signed direction components divided by 32768                     |
| Time / return        | 6-byte seconds +4-byte microseconds in header; MSOP strongest-return flag 4 in this revision |

[E1R protocol §4.3](https://robosense-robotics.github.io/product-manual/en/E1R/#43-communication-protocol). Other return labels in a generic DIFOP table do not prove selectable multi-return support for this E1R firmware.

## Hardware and connections

### Matched harness and power path <a href="#interface-description" id="interface-description"></a>

The documented sensor connector is **TE 2397179-1**, mating harness **TE 2397144-1**,6+2 contacts carrying power/wakeup and automotive Ethernet. Use the original connector-face/key and cable drawings; do not transfer M1P or EMX terminal numbers to this differently specified connector. The read manual's drawing identifies harness orientation; this procedure uses the intact approved harness, not custom retermination. [E1R §3.1](https://robosense-robotics.github.io/product-manual/en/E1R/#31-interface-description).

| Connection    | Requirement                                                                        |
| ------------- | ---------------------------------------------------------------------------------- |
| Sensor side   | Approved E1R automotive-Ethernet/power harness, correct key and fully seated seals |
| Interface box | Exact matching T 1-to-gigabit conversion and wakeup/power path                     |
| Power         | 9–16 V at E1R, through approved kit; DC5.5 × 2.1 box inlet                         |
| Wakeup        | Approved 9–16 V High path; do not drive from 3.3 V/5 V MCU pin                     |
| Host          | Ordinary gigabit RJ45 from the interface box, not directly from the sensor         |
| Cable routing | Bend radius>30 mm; at least 70 mm handling clearance at connector exit             |

The manual recommends STP automotive Ethernet, practical harness length ≤12 m and no more than three connector pairs after considering board losses. Both 3.5 m and 8 m sold kits are below that recommendation but still need routing/strain relief. Keep sensor voltage within its range despite cable drop; do not compensate beyond 16 V. [E1R §§3.1–3.3](https://robosense-robotics.github.io/product-manual/en/E1R/).

![Retained manufacturer illustration from Interface Description](<../../.gitbook/assets/image (999).png>) ![Retained manufacturer illustration from Interface Description](<../../.gitbook/assets/image (1000).png>)

### Mounting and optical clearance <a href="#product-installation-recommendations" id="product-installation-recommendations"></a>

The current manual recommends upright mounting, four M4 × 0.7 fastening points and strength class 8.8 or higher. Its reference torque is 2.7 N·m±10%, subject to the actual screw/joint validation; reference screw length is bracket thickness +3 mm with at least four engaged teeth. Inspect the matched mechanical drawing before choosing screw length or locating features.

Allow>5 mm clearance to adjacent parts, keep front/rear thermal surfaces effective and use a conductive bracket rather than an enclosing insulating shell. Reference alignment tolerances are±3 mm translation and±1.5° angular; they are installation recommendations, not a substitute for calibration. Nothing, including clear glass, should obstruct the defined optical envelope. [Mechanical/thermal/cover sections 3.4–3.7](https://robosense-robotics.github.io/product-manual/en/E1R/).

### Frames and time <a href="#coordinate-system" id="coordinate-system"></a>

Measure the E1R frame's transform to the robot, then verify a known target direction in the decoded cloud. Do not treat the signed direction-vector fields as azimuth/elevation counts. For synchronization, verify actual gPTP or L2-PTP mode and lock status; read-only `ethtool -T ACTUAL_INTERFACE` reveals host timestamp capabilities. A GPS source enters the external timing-master topology, not an invented GPS port on the sensor. [Coordinate/time chapters](https://robosense-robotics.github.io/product-manual/en/E1R/).

### Manufacturer drawings and retained diagrams

<figure><img src="../../.gitbook/assets/image (994).png" alt="RoboSense E1R Fully Solid-State LiDAR with 120° × 90° Ultra-Wide FOV for Robotics manufacturer illustration from Description"><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (995).png" alt="RoboSense E1R Fully Solid-State LiDAR with 120° × 90° Ultra-Wide FOV for Robotics manufacturer illustration from Description"><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (996).png" alt="RoboSense E1R Fully Solid-State LiDAR with 120° × 90° Ultra-Wide FOV for Robotics manufacturer illustration from Description"><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (997).png" alt="RoboSense E1R Fully Solid-State LiDAR with 120° × 90° Ultra-Wide FOV for Robotics manufacturer illustration from Description"><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (998).png" alt="RoboSense E1R Fully Solid-State LiDAR with 120° × 90° Ultra-Wide FOV for Robotics manufacturer illustration from Description"><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (1001).png" alt="RoboSense E1R Fully Solid-State LiDAR with 120° × 90° Ultra-Wide FOV for Robotics manufacturer illustration from The Connection of Interface Box"><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (1004).png" alt="RoboSense E1R Fully Solid-State LiDAR with 120° × 90° Ultra-Wide FOV for Robotics manufacturer illustration from LiDAR State Machine"><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (1005).png" alt="RoboSense E1R Fully Solid-State LiDAR with 120° × 90° Ultra-Wide FOV for Robotics manufacturer illustration from Coordinate System"><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (1006).png" alt="RoboSense E1R Fully Solid-State LiDAR with 120° × 90° Ultra-Wide FOV for Robotics manufacturer illustration from Communication Protocol"><figcaption></figcaption></figure>

_Manufacturer drawings retained from this guide. Use the stated model/revision and the original manual when interpreting connector views and dimensions._

### The Connection of Interface Box <a href="#the-connection-of-interface-box" id="the-connection-of-interface-box"></a>

The E1R sensor is **1000BASE-T1**; the matched box exposes conventional Gigabit RJ45 to the host and a **DC 5.5 × 2.1 mm** power interface. A steady green box indicator means its power path is present; if dark, check the input and cable before concluding the LiDAR is faulty. A lit box does not prove a decoded cloud.

The installation reference requires a correctly mated assembly to meet IP67/IP6K9K, at least **70 mm** hand clearance at the harness end, and STP cable suitable for 1000BASE-T1. Its cited examples are Dacra 686-3 with a **25 mm** bend radius and GGX9305 with a **12 mm** radius, subject to the cable supplier's specification. Total Ethernet harness length should be **<15 m**, with no more than **three connector pairs**; avoid moving/high-temperature routes, account for conductor loss so **9–16 V remains at the sensor**, and protect exposed runs with the specified waterproof sleeving. These are E1R harness requirements, not a pinout inferred from the similar EMX connector. The 25/12 mm bulk-cable examples and <15 m general ceiling do not relax the **>30 mm connector-exit bend radius** or the **≤12 m practical harness recommendation** after board-end losses. Apply both constraints to the actual assembly.

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/E1R/#32-interface-description).

<img src="../../.gitbook/assets/image (1002).png" alt="Retained manufacturer illustration from The Connection of Interface Box" data-size="original"> <img src="../../.gitbook/assets/image (1003).png" alt="Retained manufacturer illustration from The Connection of Interface Box" data-size="original">

### LiDAR State Machine <a href="#lidar-state-machine" id="lidar-state-machine"></a>

The matched wake-up path must provide the manual's **9–16 V high level**; this is an automotive supply-level control, not a 3.3 V GPIO. Inspect initialization/standby/sleep/fault/normal status through the supported box/viewer. A wake command or lit power indicator does not override a reported temperature, supply or communication fault; correct that condition before starting a cloud.

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/E1R/).

## Software and development resources

The OEM manual's driver appendix selects the **RSE1** decoder family for this E1R format. The reviewed core's 1200/256-byte lengths and 96 vector blocks match the manual. This establishes the specific packet path, not interchangeability with every E 1-family model/firmware. [Manual Appendix A](https://robosense-robotics.github.io/product-manual/en/E1R/), [actual decoder](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/driver/decoder/decoder_RSE1.hpp).

Use Ubuntu 22.04/ROS2 Humble with the official `rslidar_sdk`, its `rs_driver` submodule and `rslidar_msg`; the documented dependencies are PCL, yaml-cpp and libpcap. Select `RSE1` in `config/config.yaml`; the default shipped RSM1 profile is wrong for these 1200-byte packets. RSView is the manufacturer GUI; obtain the build/configuration supporting the received E1R from the official resource center. [SDK README](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/README.md).

ROS defaults use `/rslidar_points` and sensor frame `rslidar`. The default XYZI point structure drops time/ring fields expected by some fusion software. Select the documented point type deliberately and retain the clock/calibration policy with each dataset. [Config](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/config/config.yaml), [point type procedure](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/doc/howto/05_how_to_change_point_type.md).

### LiDAR Usage <a href="#lidar-usage" id="lidar-usage"></a>

Use the E1R-specific RSE1 vector decoder after a basic RSView capture. The model measures a 120° × 90° sector, so bracket/body occlusion and the defined sensor coordinate origin matter more than a generic rotating-LiDAR ring label. Preserve the actual return/timing fields and the supplied factory geometry; a successful UDP receiver is only the transport checkpoint.

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/E1R/).

### Communication Protocol <a href="#communication-protocol" id="communication-protocol"></a>

This is the E1R manual's detailed **1200-byte MSOP / 256-byte DIFOP** reference, retained as readable text/tables. The matched RSE1 implementation uses big-endian range/vector fields, 5 mm range counts and signed direction components divided by 32768. Keep the delivered protocol revision with a PCAP; the manual's default return flag and DIFOP capability codes have different roles. [Official protocol §4.3](https://robosense-robotics.github.io/product-manual/en/E1R/#43-communication-protocol).

The communication between E1R and the computer is through Ethernet, and uses UDP protocol. There are two types of output packets: MSOP packet and DIFOP packet.

All MSOP packets involved in this document are with fixed length of 1200 bytes, DIFOP packets are with fixed length of 256 bytes. E1R network parameters are configurable, and the factory default IP and fixed client port number are set as listed in the Table:

|          |               |                  |                   |
| -------- | ------------- | ---------------- | ----------------- |
|          | IP Address    | MSOP Port Number | DIFOP Port Number |
| E1R      | 192.168.1.200 | 6699             | 7788              |
| Computer | 192.168.1.102 | 6699             | 7788              |

The default MAC address of the LiDAR is initially set at the factory, and the MAC address of each LiDAR is unique.

When using the LiDAR in unicast mode, you need to set the computer's IP to the same network segment as the LiDAR, for example, 192.168.1.x (the range of x is 1\~254), and the manual's historical unicast paragraph uses subnet mask 255.255.0.0. If you don't know the network configuration information of the LiDAR, use read-only ARP/UDP capture to establish the actual addresses before changing host routes. The controlled first-run example in this guide deliberately uses 192.168.1.102/24; a broader /16 mask is not a general remedy for discovery.

The communication protocol between E1R and the computer is mainly divided into two categories. See the Table for the protocol list.

The main data stream output protocol (MSOP), encapsulates the distance, angle, reflectivity and other information measured by the LiDAR into a package and outputs it to the computer.

LiDAR information output protocol (DIFOP), outputs various configuration information of the LiDAR currently in use to the computer.

|                                    |              |                           |      |             |
| ---------------------------------- | ------------ | ------------------------- | ---- | ----------- |
| Protocol                           | Abbreviation | Function                  | Type | Packet size |
| Main Data Stream Output Protocol   | MSOP         | Output measured data      | UDP  | 1200 Bytes  |
| Device Information Output Protocol | DIFOP        | Output device information | UDP  | 256 Bytes   |

Main Data Stream Output Protocol (MSOP):

Main data Stream Output Protocol is abbreviated as MSOP.

I/O type: LiDAR output, computer analysis.

Default port number: 6699.

The MSOP packets output three-dimensional measurement related data, including laser ranging value, return reflectivity value, vertical angle, horizontal angle and time stamp.The payload length of the MSOP packet is 1200 bytes, which consists of a synchronization header of 32 bytes, a data packet of 1152 bytes (a total of 96 data blocks of 12 bytes), and a tail of 16 bytes.

Header:

The header is 32-bytes long, and is used for identification of the starting position of data, packet counting, UDP communication reservation, and time stamp storage.

|                 |           |         |            |          |
| --------------- | --------- | ------- | ---------- | -------- |
| Header(32Bytes) |           |         |            |          |
| Sync            | PktCnt    | Ver     | ReturnMode | TimeMode |
| 4 Bytes         | 2 Bytes   | 2 Bytes | 1 Byte     | 1 Byte   |
| Timestamp       | FrameSync | Res0    | LidarType  | LidarTmp |
| 10 Bytes        | 1 Byte    | 9 Bytes | 1 Byte     | 1 Byte   |

Sync: can be used as a packet inspection sequence, and the identification header is 0x55, 0xaa, 0x5a, 0xa5.

PktCnt: Packets Sequence Number, packet counting in a circular counting manner, the count value of the first data packet of each frame is 0, the count value of the last data packet of each frame is the maximum value.

Ver: version number of the UDP communication protocol.

ReturnMode: return mode flag, 4 means strongest return, which is fixed.

TimeMode: Time synchronization mode:

* 0x00: currently using the LiDAR internal timing.
* 0x02: currently using PTP E2E time synchronization mode.
* 0x03: currently using gPTP time synchronization mode.

Timestamp: store timestamps. The defined timestamp is used to record the system.

time. The high 6 bytes are the second bits, and the low 4 bytes are the microsecond bits.

FrameSync: frame synchronization state（0x00:no 0x01:yes）

Res0: reserved bit

LidarType: the type of LiDAR, default is 0x62.

LidarTmp: LiDAR’s temperature, Temp = LidarTmp – 80

Data Packet:

The data packet in the MSOP packet stores the data measured by the LiDAR, it has a total of 1152 bytes consisting of 96 data blocks, each data block has 12 bytes

|                      |        |      |                                                                                                                                |
| -------------------- | ------ | ---- | ------------------------------------------------------------------------------------------------------------------------------ |
| Data block (12Bytes) |        |      |                                                                                                                                |
| content              | offset | byte | instruction                                                                                                                    |
| TimeOffset           | 0      | 2    | The time offset of all points in the block relative to the timestamp of the packet, the time of this group of points equals to |

|                |    |   |                                                                                                                           |
| -------------- | -- | - | ------------------------------------------------------------------------------------------------------------------------- |
|                |    |   | Timestamp + time\_offset                                                                                                  |
| Radius         | 2  | 2 | In the polar coordinate system, the radial distance value of the points, the distance resolution is 5 mm                  |
| DirVectorX     | 4  | 2 | Unit direction vector X axis component of channel 1, the value ranges from -32768 to 32767, and divides by 2^15 to float. |
| DirVectorY     | 6  | 2 | Unit direction vector Y axis component of channel 1, the value ranges from -32768 to 32767, and divides by 2^15 to float. |
| DirVectorZ     | 8  | 2 | Unit direction vector Z axis component of channel 1, the value ranges from -32768 to 32767, and divides by 2^15 to float. |
| Intensity      | 10 | 1 | Reflection intensity value of the channel 1 points, the value range is 0\~255                                             |
| PointAttribute | 11 | 1 | Attribute of the channel 1 point, 1 indicates normal, 2 indicates noisy point,                                            |

{% hint style="info" %}
Related calculation specification:

Calculation of the radial distance: (Radius is 2-byte long, the unit is millimeter, and the resolution is 5 mm.)

Get the hexadecimal number of the radius value of a charnel in the data packet: R1 is 0x03, R2 is 0xfc

0x03 is the high digit of the distance, converted to decimal is 3, 0xfc is the low digit of the distance, converted into decimal is 252.

Therefore: the radial distance of this channel=R1\*256+R2=3\*256+252=1020.

According to the resolution of the coordinates, it is converted to meters: 1020\*0.005=5.10 m.

Therefore, the radial distance of this channel in the corresponding elevation and azimuth direction is 5.1 m.

Calculation of XYZ coordinates:

For the supplied unit direction vector, calculate `x = range_m * vx`, `y = range_m * vy`, `z = range_m * vz`, where each signed 16-bit vector component is divided by 32768. Retain the point TimeOffset before motion compensation.
{% endhint %}

Tail:

The frame tail contains parameters used by LiDAR E2E Profile4

|            |        |      |              |
| ---------- | ------ | ---- | ------------ |
| content    | offset | byte | instruction  |
| Res1       | 1184   | 4    | Reserved     |
| DataLength | 1188   | 2    | 04 B0        |
| Counter    | 1190   | 2    | 00 00\~FF FF |
| DataId     | 1192   | 4    | 00 00 0E 5C  |
| Crc32      | 1196   | 4    |              |

LiDAR Information Output Protocol is abbreviated as DIFOP:

I/O type: LiDAR output, computer read.

Default port number: 7788.

DIFOP is an "output-only" protocol to periodically send the LiDAR serial number (S/N), firmware version information, host computer driver compatibility information, network configuration information, calibration information, operating status, and fault diagnosis information to users. By reading DIFOP, users can learn specific information of various parameters of the LiDAR currently in use.

|                        |        |      |                                                                                                                                                                         |
| ---------------------- | ------ | ---- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| DIFOP Packet(256Bytes) |        |      |                                                                                                                                                                         |
| content                | offset | byte | instruction                                                                                                                                                             |
| DifopHeader            | 0      | 8    | DIFOP recognition head                                                                                                                                                  |
| Res0                   | 8      | 8    | Reserved                                                                                                                                                                |
| SW Version             | 16     | 3    | LIDAR SW version information                                                                                                                                            |
| Res1                   | 19     | 1    | Reserved                                                                                                                                                                |
| SN                     | 20     | 6    | Serial number                                                                                                                                                           |
| Res2                   | 26     | 18   | Reserved                                                                                                                                                                |
| LocalIP                | 44     | 4    | LIDAR IP source address                                                                                                                                                 |
| NetMask                | 48     | 4    | Subnet mask                                                                                                                                                             |
| MacAddress             | 52     | 6    | LIDAR IP local Mac address                                                                                                                                              |
| MsopRemoteIp           | 58     | 4    | Msop remote IP address                                                                                                                                                  |
| MsopLocalPort          | 62     | 2    | Msop local port number                                                                                                                                                  |
| MsopRemotePort         | 64     | 2    | Msop Remote port number                                                                                                                                                 |
| DifopRemoteIp          | 66     | 4    | Difop Remote IP address                                                                                                                                                 |
| DifopLocalPort         | 70     | 2    | Difop Local port number                                                                                                                                                 |
| DifopRemotePort        | 72     | 2    | Difop Remote port number                                                                                                                                                |
| Res3                   | 74     | 25   | Reserved                                                                                                                                                                |
| FrequecySetting        | 99     | 1    | LIDAR frame rate setting                                                                                                                                                |
| ReturnMode             | 100    | 1    | LIDAR echo information： 0x00: FarthestWave 0x04: StrongestWave (Default) 0x07: NearestWave 0x08: 2ndStrongestWave 0x09: StrongestFarthestWave 0x0A: NearestFarthestWave |

|                |     |     |                                                                               |
| -------------- | --- | --- | ----------------------------------------------------------------------------- |
|                |     |     | 0x0B: Strongest2ndStrongestWave                                               |
| TimesyncMode   | 101 | 1   | Time Synchronization Mode: 0x0: Internal 0x2: E2E L2 0x3: GPTP                |
| TimesyncStatus | 102 | 1   | Time Syne Status: 0x00: failed 0x01: success 0x02: timeout                    |
| TimeStatus     | 103 | 10  | Timestamp: 0-5 bytes: Second 6-9 bytes: MicroSecond                           |
| PHYMode        | 113 | 1   | PHY Mode: 0x00: auto-negotiation 0x01: master 0x02: slave other: same as 0x00 |
| Res4           | 114 | 142 | Reserved                                                                      |

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/E1R/#43-communication-protocol).

<img src="../../.gitbook/assets/image (1007).png" alt="Retained manufacturer illustration from Communication Protocol" data-size="original">

### SDK configuration, recording and replay behavior

The pinned SDK uses one shared `common` block and one `lidar` list entry per sensor. For **E1R**, keep **`lidar_type:RSE1`** and the model-specific network/packet revision above. The receive-port baseline is **6699/7788; enable an IMU port only for an actually supported output**; these are not permission to transfer a cable, wake signal or decoder from a similar model.

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

### Native driver API and callback backpressure

A native C++ integration uses the pinned `LidarDriver<PointCloud>` API: register the free-cloud/completed-cloud callbacks and exception callback, populate `RSDriverParam` with this model's decoder/input settings, check `init()` and `start()` Boolean results, then call `stop()` to join the acquisition threads. `regPacketCallback` exposes packets separately from decoded clouds, while `getTemperature`, `getDeviceInfo` and `getDeviceStatus` return a Boolean indicating whether the requested information is available. A valid API method does not mean every model populates every field. [Public native API](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/api/lidar_driver.hpp).

The user's callbacks execute on the driver's decoding thread. Queue the completed cloud for a separate processing thread and recycle buffers after consumption; avoid mapping, file compression or slow network calls inside the callback. The documented consequence of blocking is **`ERRCODE_PKTBUFOVERFLOW` and discarded packets**, which can resemble a bad Ethernet link. Separate link/capture loss from application backlog before changing the sensor's power or calibration. Native `decodePacket` can consume an externally supplied packet source, but still needs the correct model framing and calibration. libpcap is needed for native PCAP input, Eigen for internal transforms, and PCL/Boost for the optional visualization tool; they are not all intrinsic requirements of every receive-only application. [Thread ownership and buffer queues](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/doc/intro/03_thread_model.md), [native dependencies and demo build options](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/README.md).

### Controlled PTP/gPTP timing and GPS-master topology

For **E1R**, time-master commissioning is separate from first cloud acquisition. The E1R source distinguishes IEEE 1588v2 Layer-2 E2E from 802.1AS Layer-2 P2P gPTP. Its option glosses contain translation errors; match the actual linuxptp help/configuration and transport rather than copy the prose labels blindly.

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

For GPS-referenced time, the documented topology is **GPS → compatible external gPTP grandmaster → Ethernet/converter → sensor**. Consult that grandmaster's actual GPS connector/electrical/time interface; do not fabricate direct GPS UART/PPS wiring onto an automotive connector. Check grandmaster absolute time as well as the sensor's lock, since a slave can follow a wrong but valid-looking master. [Exact model timing/topology source](https://robosense-robotics.github.io/product-manual/en/E1R/).

### RSView recording, replay, export and measurement

Use a Viewer release supporting the exact **E1R** packet profile. A practical comparison keeps original packets separate from exported points:

1. Verify the live scene, selected decoder/profile, time mode and receive ports. For M1P, the manual uses the **RSM1** profile and says its emitted angles are already calibrated; its MEMS correction slot is not another serial calibration to apply.
2. Start a short raw **PCAP** recording containing measurement and status/calibration traffic; retain serial/firmware, receive configuration and any external time source. **PCAPNG is not supported** by this manual's RSView import path.
3. Stop the live source and open the saved PCAP. Compare a fixed target and frame orientation with the live result. Inspect the spreadsheet/table view for actual coordinates, range and intensity rather than rely only on point color.
4. Export the selected points to CSV for numeric analysis. The E1R manual adds LAS export from **RSView 4.3.11**; do not substitute Airy’s earlier LAS version threshold. Preserve the raw PCAP because exported XYZ cannot reconstruct missing protocol flags or factory status.
5. Use Viewer’s measurement/display tools to compare a known stationary separation and alternate XYZ/range/elevation/azimuth coloring. Treat a visual measurement as a diagnostic, not a certified range-accuracy test.

**Expected result:** replay reproduces the same static geometry and the export contains the selected measurements with a saved coordinate/time interpretation. If packets replay but geometry differs, compare decoder revision, calibration and return mode before changing hardware. [Model-specific RSView and raw-data workflows](https://robosense-robotics.github.io/product-manual/en/E1R/).

### Bracket strength, stone impact and thermal contact requirements

The E1R OEM installation guidance adds mechanical criteria beyond clearing the optical field. Mounting contact-pad flatness should be **≤0.5 mm**. For the source's structural design check, maximum shock stress should remain **below two-thirds of tensile strength**, and vibration **1σ RMS stress below one-fifth**. These are OEM design recommendations requiring actual load/material/fixture validation; passing a nominal bracket-thickness rule does not establish fatigue life.

Use an aluminum heat path with conductivity **>50 W/(m·K)**, suitable contact area and airflow. Evaluate front/rear heat dissipation together with the existing >5 mm clearance rule; a close-fitting cover can preserve optical clearance yet impede cooling. The protective-cover/window edge must also be protected against stone impact without letting the bracket mask the scan. Keep the received revision's optical keep-out and contact surfaces, and use its mounting/CAD drawing for fabrication rather than a similar solid-state housing. [Official E1R mechanical, thermal and impact guidance §§3.4.4–3.7](https://robosense-robotics.github.io/product-manual/en/E1R/).

## Getting started

### Bring-up from the prewired kit <a href="#rsview" id="rsview"></a>

1. Confirm the E1R label and exact kit length. For sensor-only purchases, obtain the complete compatible interface/power chain first. With power removed, connect the keyed sensor harness to the matching interface box and its ordinary gigabit RJ45 to the host.
2. Configure the dedicated host adapter to `192.168.1.102/24` for the documented default `.200` sensor. This isolated direct-link setting matches the factory address pair; the manual also discusses broader masks for packet diagnosis. Do not reconfigure an unrelated management link.
3. Apply the approved supply/wakeup path. Confirm box power/link indicators and Normal Run rather than assuming power means the sensor woke.
4. In compatible RSView choose the E1R-provided sensor configuration/RSE1 packet family. Confirm host destination and ports 6699/7788. Look for an updating point cloud and a known stationary target.
5. Save a short PCAP, then replay it in the same profile. Record serial, firmware, host/ports, viewing software and interface-box identity.

**Expected result:** continuous decoded cloud from the identified E1R and a reproducible capture. Packets without coherent geometry establish only transport. [Manual §§3.2,4.2](https://robosense-robotics.github.io/product-manual/en/E1R/).

### Original read-only vector checkpoint

Close other applications using UDP 6699. Save as `e1r_first_vector.py` and run Python 3 on the configured host. It samples one normal point from the documented packet; it does not send commands or replace the full decoder's CRC/integrity handling.

```python
import math
import socket
import struct
import time

deadline = time.monotonic() + 8.0
found = False
with socket.socket(socket.AF_INET, socket.SOCK_DGRAM) as receiver:
    receiver.bind(("0.0.0.0", 6699))
    receiver.settimeout(0.25)
    while not found and time.monotonic() < deadline:
        try:
            packet, peer = receiver.recvfrom(65535)
        except socket.timeout:
            continue
        if len(packet) != 1200 or packet[:4] != bytes.fromhex("55 aa 5a a5"):
            continue
        for offset in range(32, 1184, 12):
            dt, raw_range, dx, dy, dz, intensity, attribute = struct.unpack_from(
                ">HHhhhBB", packet, offset)
            if attribute != 1 or raw_range == 0:
                continue
            direction = [v / 32768.0 for v in (dx, dy, dz)]
            distance = raw_range * 0.005
            xyz = [distance * v for v in direction]
            print("source", peer[0], "range_m", distance, "xyz_m", xyz,
                  "direction_norm", math.sqrt(sum(v*v for v in direction)),
                  "intensity", intensity, "offset_us", dt)
            found = True
            break
if not found:
    raise SystemExit("No normal E1R vector observed; inspect profile and traffic")
```

**Expected result:** one nonzero range/XYZ sample in metres and a direction norm near one. Treat it as a parser/units checkpoint; do not interpret a single sample as a calibrated distance test or obstacle decision. Unexpected sizes or fields require the exact received protocol. [Vector definitions](https://robosense-robotics.github.io/product-manual/en/E1R/#4312-data-packet).

### ROS2 live decoding

With ROS2 Humble/PCL/yaml-cpp/libpcap/colcon installed, create a new workspace and use the reviewed SDK snapshot:

```bash
mkdir -p ~/e1r_ws/src
cd ~/e1r_ws/src
git clone https://github.com/RoboSense-LiDAR/rslidar_sdk.git
cd rslidar_sdk
git checkout 8b4b4b7ff910799260347821084c59e1c73d50d5
git submodule update --init --recursive
cd ~/e1r_ws/src
git clone https://github.com/RoboSense-LiDAR/rslidar_msg.git
source /opt/ros/humble/setup.bash
cd ~/e1r_ws
colcon build
source install/setup.bash
```

Edit `src/rslidar_sdk/config/config.yaml`: live `msg_source:1`,`lidar_type:RSE1`, ports 6699/7788 and `send_point_cloud_ros:true`. Start `ros2 launch rslidar_sdk start.py`; in another sourced terminal run `ros2 topic info /rslidar_points --verbose` and `ros2 topic hz /rslidar_points`. Set the RViz fixed frame to the actual sensor frame first.

**Expected result:** advancing PointCloud2 frames at the configured rate, with a coherent static target. Compare the saved PCAP replay using `msg_source:3`, same model/ports and `pcap_repeat:false` before adding navigation or sensor fusion. [Live/replay procedures](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/doc/howto/06_how_to_decode_online_lidar.md).

## Troubleshooting and FAQs

| Symptom                          | Checks and bounded recovery                                                                                                |
| -------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| Power but no output              | Actual 9–16 V at sensor, wakeup/interface box and T1 link; do not probe a wakeup pin with MCU logic                        |
| Ordinary RJ45 link but no sensor | Matched conversion box and sensor-side cable; RJ45 link alone is not T1 link proof                                         |
| No host packets                  | Actual target IP, isolated adapter/subnet,6699/7788, firewall and receive ownership; capture ARP to learn changed settings |
| Packets but bad/no geometry      | RSE1 selection,1200-byte format, normal/noise attribute and signed-vector scaling; not RSM1 polar angles                   |
| Close targets disappear          | Driver distance filter versus 0.1 m blind zone, target reflectivity and optical cover occlusion                            |
| Time fusion fails                | Actual sync profile/lock, master state, PHC capability and measured frame transform                                        |
| Thermal degradation              | Conductive bracket, front/rear heat path,>5 mm clearance and operating temperature                                         |

For recovery, retain capture/logs/settings, close the current receiver and restart the matched kit only after power/wakeup checks. The accessible manual does not provide a universal public firmware-flash command or pin-recovery short; do not invent one. Use an exact manufacturer release/procedure for the unit if an upgrade is required. Protect/clean the optical surface as documented and keep dry, cushioned packaging for storage/transport. [OEM manual](https://robosense-robotics.github.io/product-manual/en/E1R/).

### Storage <a href="#storage" id="storage"></a>

Keep E1R indoors, dry and at normal storage temperature, protected from corrosion, impacts and exposure beyond the assembly's ingress rating. The model specification's storage interval is a limit, not a recommendation to store routinely at an extreme. Handle the optical window and connector without dropping or loading them, and inspect the sensor/components/packaging every **three months**. Preserve moisture- and shock-resistant original packaging for transport. Firmware upgrade is a separate procedure and does not belong to storage. [Manufacturer storage §6.2](https://robosense-robotics.github.io/product-manual/en/E1R/#62-storage).

## Downloads and technical documents

| Resource                                                                                                                                                 | Scope                                                                                              |
| -------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| [Complete E1R manual](https://robosense-robotics.github.io/product-manual/en/E1R/)                                                                       | Optical envelope, connector/harness, thermal/mounting, time,1200/256-byte protocol and maintenance |
| [Mechanical Appendix B](https://robosense-robotics.github.io/product-manual/en/E1R/#appendix-b-mechanical-drawings)                                      | Actual dimensioned drawing; do not infer connector orientation from a render                       |
| [RSE1 decoder](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/driver/decoder/decoder_RSE1.hpp) | Concrete vector-packet layout                                                                      |
| [ROS2 SDK](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/README.md)                                       | Build, configuration, live/PCAP examples                                                           |
| [RoboSense resources](https://www.robosense.ai/en/resources)                                                                                             | Compatible RSView/current documentation; firmware access may require manufacturer request          |

The connector/harness figures were inspected; the original attachments/diagrams below are preserved. A complete custom harness-terminal definition must be obtained for any retermination; the first-result path uses the supplied intact E1R harness.

### Documents <a href="#documents" id="documents"></a>

| Exact retained attachment                                           | Verified format / bytes | Purpose                                                                                                      |
| ------------------------------------------------------------------- | ----------------------- | ------------------------------------------------------------------------------------------------------------ |
| [E1R User Guide.pdf](<../../.gitbook/assets/E1R User Guide.pdf>)    | PDF / 2,459,458         | Model-specific integration manual; compare its revision with the current online reference                    |
| [E1\_Certification.zip](../../.gitbook/assets/E1_Certification.zip) | ZIP / 19,790,142        | Original certification bundle; the E1 filename alone does not establish every certificate's E1R/system scope |

{% file src="../../.gitbook/assets/E1R User Guide.pdf" %}

{% file src="../../.gitbook/assets/E1_Certification.zip" %}

### 3D model <a href="#id-3d-model" id="id-3d-model"></a>

[Robosense E1R 3D model.zip](<../../.gitbook/assets/Robosense E1R 3D model.zip>), **ZIP, 7,050,594 bytes**, is the retained E1R CAD archive. Use it together with the matching optical-envelope and mounting drawings to check roof/bumper/bracket occlusion and connector hand clearance. File identity/size are verified; internal CAD solids have not been opened or dimensionally tested here.

{% file src="../../.gitbook/assets/Robosense E1R 3D model.zip" %}

## References and validation

Reviewed **24 November 2026**: exact sensor/3.5 m/8 m SKUs, current E1R manual and matched RSE1 packet decoder/ROS SDK. The vector sampler is original and intentionally read-only.

**Compilation, RSView/ROS execution, firmware updates, electrical/wakeup tests and physical sensing measurements: not run.** Source and syntax review do not imply hardware validation.

* [E1R complete official online manual](https://robosense-robotics.github.io/product-manual/en/E1R/) — current 24 Nov 2026.
* [RoboSense ROS2 supported platform and build](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/README.md) — commit 8b4b4b7ff910799260347821084c59e1c73d50d5.
* [E 1-family decoder matched to E1R 1200-byte vector packets](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/driver/decoder/decoder_RSE1.hpp) — commit 897b14d3bdb6186a75df27ba51b65b5bd5557723.
* [RSE1 model and UDP/ROS config](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/config/config.yaml) — commit 8b4b4b7ff910799260347821084c59e1c73d50d5.
* [ROS2 live decoder setup](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/doc/howto/06_how_to_decode_online_lidar.md) — commit 8b4b4b7ff910799260347821084c59e1c73d50d5.
* [Exact E1R sensor/3.5 m/8 m options and BOM](https://openelab.io/products/robosense-e1r-solid-state-lidar) — 23 Nov catalog; public page read 24 Nov 2026.

### Additional established references

* [http://www.robosense.ai/resource](http://www.robosense.ai/resource)
