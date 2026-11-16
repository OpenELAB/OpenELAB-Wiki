# Robosense EMX

Product link: [https://openelab.io/products/robosense-emx-192-beam-automotive?variant=45731804414150](https://openelab.io/products/robosense-emx-192-beam-automotive?variant=45731804414150)

## Robosense EMX 192-Beam Automotive-Grade Digital LiDAR Engineering Guide

The Robosense EMX is a compact 192-beam automotive-grade digital LiDAR for high-density 3D perception, ADAS research, robotics, AGV/AMR navigation, mapping, and vehicle perception test benches. This OpenELAB wiki page focuses on engineering setup: power, Ethernet wiring, RSView validation, MSOP/DIFOP packet flow, mounting checks, and practical integration notes. The specifications below prioritize `RS-EMX_UserGuide_V1.0.8_EN.pdf`; where the OpenELAB product listing differs, the conflict is called out for final confirmation before production design.

### Overview

The EMX outputs point-cloud data through Ethernet UDP packets. The main point-cloud stream uses MSOP packets, while device information, status, network parameters, synchronization state, and fault fields are reported through DIFOP packets. For bench testing, the accessory interface box converts the LiDAR-side 1000BASE-T1 automotive Ethernet interface to a PC-side RJ45 Gigabit Ethernet connection.

Recommended users include robotics engineers, autonomous vehicle researchers, perception algorithm teams, mapping developers, and system integrators who need a dense mid-range LiDAR with a compact envelope and automotive-style wiring.

![EMX product structure](<../../.gitbook/assets/product structure.png>)EMX product structure

### Key Features

* 192-line digital LiDAR architecture
* Up to 2.88 million points per second
* Ethernet UDP data output
* MSOP point-cloud stream and DIFOP device-information stream
* 1000BASE-T1 vehicle Ethernet interface on the LiDAR side
* Interface box with RJ45 Gigabit Ethernet connection for PC-side testing
* gPTP/PTP time synchronization support depending on firmware and configuration
* IP67/IP6K9K protection rating
* Operating temperature range from -40 C to +85 C

### Specifications

| Item                   | Engineering value from user guide                                                           | Product-listing value to verify         |
| ---------------------- | ------------------------------------------------------------------------------------------- | --------------------------------------- |
| Product                | Robosense EMX 192-Beam Automotive-Grade Digital LiDAR                                       | Same product family                     |
| Vendor on OpenELAB     | RoboSense                                                                                   | RoboSense                               |
| OpenELAB SKU           | RS-EMX for only LiDAR; RS-EMX-8m for accessory kit; RS-EMX-kit for LiDAR with accessory kit | Same                                    |
| Lines / beams          | 192                                                                                         | 192                                     |
| Measurement range      | 1.5 m to 200 m                                                                              | 300 m maximum range is listed           |
| Range reference        | 200 m at 10% NIST reflectance                                                               | Not specified in listing                |
| Typical accuracy       | +/- 5 cm at 1 sigma                                                                         | Not specified in listing                |
| Horizontal FOV         | 120 deg (-60 deg to +60 deg)                                                                | 140 deg maximum FOV is listed           |
| Horizontal resolution  | 0.08 deg                                                                                    | 0.08 deg                                |
| Vertical FOV           | 20 deg (-12 deg to +8 deg)                                                                  | 20 deg                                  |
| Vertical resolution    | 0.1 deg                                                                                     | 0.1 deg                                 |
| Frame rate             | 10 Hz                                                                                       | 20 Hz maximum frame rate is listed      |
| Blind zone             | <= 1.5 m                                                                                    | Not specified in listing                |
| Point output           | 2,880,000 pts/s                                                                             | 2.88 million pts/s                      |
| Point-stream bandwidth | 97.4 Mbps                                                                                   | Not specified in listing                |
| Data output            | 1000BASE-T1 Ethernet                                                                        | Ethernet-based kit described            |
| Data protocol          | UDP over Ethernet                                                                           | Not specified in listing                |
| Point data contents    | 3D coordinates, reflection intensity, timestamps                                            | Not specified in listing                |
| Operating voltage      | 9-16 VDC                                                                                    | Not specified in listing                |
| Power consumption      | 10 W                                                                                        | Not specified in listing                |
| Dimensions             | Depth 102.5 mm x width 110 mm x height 30.4 mm                                              | 120 mm x 80 mm x 30 mm is listed        |
| Weight                 | 500 g +/- 20 g, excluding data cable                                                        | Product variant shipping weights differ |
| Operating temperature  | -40 C to +85 C                                                                              | Not specified in listing                |
| Storage temperature    | -40 C to +105 C                                                                             | Not specified in listing                |
| Protection rating      | IP67 / IP6K9K                                                                               | Not specified in listing                |
| Wake-up method         | 1-pin hard-line wake-up                                                                     | Not specified in listing                |

### Hardware Architecture

The bench-test setup has four main parts:

| Block                          | Function                                                                            |
| ------------------------------ | ----------------------------------------------------------------------------------- |
| EMX LiDAR                      | Captures 3D range, intensity, beam, and timestamp data                              |
| Vehicle Ethernet power harness | Carries power, wake-up, and 1000BASE-T1 differential Ethernet                       |
| Interface box                  | Converts 1000BASE-T1 to RJ45 Gigabit Ethernet and provides power/wake-up control    |
| Host computer                  | Receives MSOP/DIFOP UDP packets, runs RSView, Wireshark, SDK, ROS, or custom parser |

Use a regulated DC supply and confirm polarity before power-up. At 12 V input and 10 W nominal power, reserve at least 0.833 A; add margin for startup and bench equipment losses.

### Mechanical Installation

Mount the EMX on a rigid, low-vibration surface. Keep the optical window clear, avoid connector strain, and reserve space for cable bend radius. Use the mechanical drawing below when checking the envelope, mounting direction, and reserved space.

![EMX mechanical dimensions](<../../.gitbook/assets/mechanical dimensions.png>)EMX mechanical dimensions

The LiDAR coordinate origin is defined at the optical center. Point-cloud packets include the measured range and the XYZ components of a unit direction vector. Cartesian coordinates can be calculated as:

```
X = range * direction_vector_X
Y = range * direction_vector_Y
Z = range * direction_vector_Z
```

![EMX coordinate system](<../../.gitbook/assets/coordinate system.png>)EMX coordinate system

### Wiring And Pinout

The EMX uses a combined vehicle Ethernet and power connector on the LiDAR side. For PC testing, the accessory interface box converts the LiDAR-side automotive Ethernet connection to an RJ45 Gigabit Ethernet connection.

![Vehicle Ethernet power harness](<../../.gitbook/assets/vehicle ethernet power harness.png>)Vehicle Ethernet power harness

#### Vehicle Ethernet Power Harness

| J1 pin | Definition    | Connected side |
| ------ | ------------- | -------------- |
| 1      | GND           | J3 pin 1       |
| 2      | Wakeup        | J3 pin 6       |
| 3      | Not connected | J3 pin 3       |
| 4      | Battery+      | J3 pin 2       |
| 5      | Not connected | J3 pin 4       |
| 6      | Not connected | J3 pin 5       |
| 7      | 1000BASE-T1 N | J2 pin 1       |
| 8      | 1000BASE-T1 P | J2 pin 2       |

#### Interface Box

![EMX interface box](<../../.gitbook/assets/interface box.png>)EMX interface box

| Interface | Connector                | Function                                       |
| --------- | ------------------------ | ---------------------------------------------- |
| J1        | MOLEX 43045-0600         | Provides LiDAR power and wake-up signal output |
| J2        | Amphenol NTBM11R1U01110T | 1000BASE-T1 vehicle Ethernet interface         |
| J3        | DC power connector       | Power input                                    |
| J4        | Switch                   | Wake-up signal control                         |
| J5        | RJ45                     | 1000BASE-TX industrial Ethernet                |

The interface box uses a standard DC 5.5 x 2.1 power connector. When power is connected correctly, the green indicator on the interface box remains on. If the indicator is off, check input voltage, polarity, cable continuity, and connector seating first.

#### TE Connector Pin Definition

![TE connector pin definition](<../../.gitbook/assets/te connector pin definition.png>)TE connector pin definition

| Pin | Definition           |
| --- | -------------------- |
| 1   | GND                  |
| 2   | Wakeup (KL15)        |
| 3   | Not connected        |
| 4   | Battery+             |
| 5   | Not connected        |
| 6   | Not connected        |
| D1  | TRX\_N (1000BASE-T1) |
| D2  | TRX\_P (1000BASE-T1) |

### Software And Setup Workflow

Factory default network settings from the user guide:

| Device | IP address    | MSOP port | DIFOP port |
| ------ | ------------- | --------- | ---------- |
| EMX    | 192.168.1.200 | 6699      | 7788       |
| PC     | 192.168.1.102 | -         | -          |

![EMX quick connection](<../../.gitbook/assets/quick connection.png>)EMX quick connection

1. 1\. Connect the LiDAR to the interface box using the in-vehicle Ethernet power cable harness.
2. 2\. Connect the PC to the interface box through the RJ45 Gigabit Ethernet port.
3. 3\. Power on the interface box and confirm that the green indicator remains lit.
4. 4\. Set the PC Ethernet adapter to a static IP on the same subnet, for example `192.168.1.102` with subnet mask `255.255.255.0`.
5. 5\. Use Wireshark to confirm that MSOP packets are received on UDP port `6699` and DIFOP packets on UDP port `7788`.
6. 6\. Open RSView and verify live point-cloud display before moving to SDK, ROS, ROS 2, or custom parsing.

The EMX uses a static ARP list. If the host computer is replaced after normal communication has already been established, power-cycle the LiDAR before connecting it to the new host.

### RSView Validation

RoboSense RSView can visualize real-time EMX point-cloud data and replay recorded PCAP files. It supports Windows 64-bit and Ubuntu 18.04 or later.

RSView can be used for:

* Real-time Ethernet data display
* Recording real-time data to PCAP
* Replaying PCAP files
* Coloring point clouds by distance, time, horizontal angle, reflectivity, or beam number
* Viewing point data in table form
* Exporting point-cloud data as CSV
* Exporting LAS files in RSView 3.1.3 or later
* Measuring distance
* Displaying multiple replay frames
* Showing or hiding individual beams
* Clipping the displayed point cloud

Keep the RSView extraction path and configuration path free of Chinese characters to avoid display or runtime issues.

### Communication Protocol

The EMX communicates with the host computer over Ethernet using UDP. The main packet types are MSOP and DIFOP.

| Protocol | Function                             | Direction     | Default port | Payload size |
| -------- | ------------------------------------ | ------------- | ------------ | ------------ |
| MSOP     | Main point-cloud data stream         | LiDAR to host | 6699         | 812 bytes    |
| DIFOP    | Device information and status stream | LiDAR to host | 7788         | 256 bytes    |

#### MSOP Packet Notes

| Field             | Notes                                              |
| ----------------- | -------------------------------------------------- |
| Header ID         | `0x55 0xAA 0x5A 0xA5`                              |
| Packet count      | Starts at 1 for each frame; 1520 packets per frame |
| Return mode       | Double, strongest, last, or nearest echo           |
| Time mode         | Internal timing, PTP, or gPTP                      |
| Timestamp         | Seconds plus microseconds                          |
| LiDAR type        | Default `0x42`                                     |
| Temperature       | Raw value converted as `Temp = Device_Temp - 80`   |
| Point data        | 192 points per packet, 4 bytes each                |
| Radius resolution | 5 mm                                               |
| Intensity         | 0-255                                              |
| Point attribute   | Normal point or noise point                        |

#### DIFOP Packet Notes

| Field            | Notes                                                           |
| ---------------- | --------------------------------------------------------------- |
| Work mode        | Init, wait normal, reset, standby, sleep, fault, normal         |
| Frame rate       | `0x0A` for 10 Hz, `0x14` for 20 Hz                              |
| Wave mode        | Nearest/farthest, strongest, farthest, nearest, histogram, gray |
| Time sync mode   | Internal source timer, PPS, E2E L2, gPTP, P2P L4                |
| Time sync status | Failed, success, or timeout                                     |
| Source IP        | Default `192.168.1.200`                                         |
| Destination IP   | Default `192.168.1.102`                                         |
| Fault level      | No fault, FL1, FL2, or FL3                                      |

### Engineering Setup Checklist

* Confirm the purchased variant: only LiDAR, accessory kit, or LiDAR with accessory kit.
* Confirm whether the project should follow the user guide specifications or the OpenELAB listing values where they differ.
* Use the interface box for first bring-up unless the system already has a compatible 1000BASE-T1 interface.
* Set the host PC to `192.168.1.102/24` for the first test.
* Capture UDP `6699` and `7788` traffic in Wireshark before debugging RSView or SDK code.
* Check power polarity, wake-up wiring, and the interface-box indicator before connecting to a vehicle or robot controller.
* Record a short PCAP after bring-up; it is useful for software integration and regression tests.
* Validate time synchronization mode before multi-sensor fusion, SLAM, or ADAS dataset capture.

### Best Practices And Limitations

* Do not design the mechanical bracket from product-listing dimensions alone; use the final drawing or measured hardware because the listing and user guide dimensions differ.
* Do not assume the maximum range, horizontal FOV, or maximum frame rate until the exact EMX firmware/configuration is confirmed.
* Keep the optical cover clean and avoid wiping mud or solid particles directly across the cover.
* Prefer direct Ethernet connection during first bring-up to avoid router DHCP conflicts and broadcast traffic.
* If packet loss appears, test with a known-good Gigabit Ethernet adapter and a short direct cable before changing LiDAR settings.
* Public CAD drawings, firmware download pages, and an EMX-specific official product page were not confirmed during this review; request them before final vehicle packaging or production release.
* No support email, phone number, or contact block is included in this wiki page.

### Cleaning And Maintenance

Recommended cleaning materials:

* Clean dust-free cloth
* Neutral cleaning solution at moderate temperature, such as soapy water, distilled water, or 99% ethanol

For light dust, lightly wipe the surface with a dust-free cloth moistened with neutral solution, then dry it with a clean cloth. For mud or solid foreign material, rinse with clean water first. Do not wipe mud directly across the protective cover, because it may scratch the surface.

### Troubleshooting

| Symptom                                                    | Checks                                                                                                                                                                                                           |
| ---------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Interface-box indicator is off or flashing                 | Check power wiring, connector tightness, and harness damage                                                                                                                                                      |
| LiDAR keeps restarting                                     | Check input polarity, voltage, and current; at 12 V input, current should be at least 0.833 A                                                                                                                    |
| Wireshark receives packets but RSView shows no point cloud | Disable or allow RSView through the firewall; verify PC IP matches the LiDAR destination IP; confirm RSView sensor network settings; confirm the RSView path has no Chinese characters; confirm packets are MSOP |
| Frequent packet loss                                       | Check for network conflicts, broadcast traffic, host performance limits, and Ethernet interface performance; test with a direct PC connection                                                                    |
| gPTP synchronization fails                                 | Confirm firmware support, gPTP master compatibility, and master operating status                                                                                                                                 |
| No data through a router                                   | Disable DHCP on the router or set the LiDAR IP correctly inside the router network                                                                                                                               |

If troubleshooting does not resolve the issue, keep the device powered off and review the latest user guide before further operation.

### Project References And Application Ideas

* ROS or ROS 2 perception bring-up using RoboSense SDK/driver packages, then publish point clouds into the robot middleware pipeline.
* ADAS or autonomous-driving research datasets that combine EMX point clouds with camera, GNSS/INS, radar, or wheel-odometry data.
* AGV/AMR obstacle detection in warehouses where dense mid-range 3D coverage is more useful than a 2D safety scanner alone.
* Mapping and localization experiments using PCL filters, voxel grids, ground segmentation, ICP/NDT registration, or SLAM pipelines.
* Multi-LiDAR timestamp experiments using PTP/gPTP, with Wireshark and PCAP files used to verify packet timing.

### Resources

| Resource               | Link                                                                                                                                                                           | Notes                                                                                    |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------- |
| OpenELAB product page  | [https://openelab.io/products/robosense-emx-192-beam-automotive?variant=45731804414150](https://openelab.io/products/robosense-emx-192-beam-automotive?variant=45731804414150) | Product title, variants, listing specs, and packing-list context                         |
| EMX user guide PDF     | [https://www.generationrobots.com/media/robosense-emx-user-guide.pdf](https://www.generationrobots.com/media/robosense-emx-user-guide.pdf)                                     | Public PDF copy checked during review; local file used: `RS-EMX_UserGuide_V1.0.8_EN.pdf` |
| RoboSense rslidar\_sdk | [https://github.com/RoboSense-LiDAR/rslidar\_sdk](https://github.com/RoboSense-LiDAR/rslidar_sdk)                                                                              | Official GitHub SDK for RoboSense LiDAR integration                                      |
| RoboSense rs\_driver   | [https://github.com/RoboSense-LiDAR/rs\_driver](https://github.com/RoboSense-LiDAR/rs_driver)                                                                                  | Official lower-level RoboSense driver repository                                         |
| Autoware documentation | [https://autowarefoundation.github.io/autoware-documentation/](https://autowarefoundation.github.io/autoware-documentation/)                                                   | Reference ecosystem for autonomous-driving perception integration                        |
| Point Cloud Library    | [https://pointclouds.org/](https://pointclouds.org/)                                                                                                                           | Reference ecosystem for point-cloud filtering, registration, and processing              |

### FAQ

#### What is the Robosense EMX used for?

It is used for dense 3D perception in ADAS research, robotics, AGV/AMR navigation, mapping, obstacle detection, and point-cloud software development.

#### What ports does the EMX use by default?

The user guide lists UDP port `6699` for MSOP point-cloud packets and UDP port `7788` for DIFOP device-information packets.

#### What default IP address should I use during first bring-up?

Use `192.168.1.200` for the EMX and set the PC to `192.168.1.102/24`, unless the device has already been reconfigured.

#### Does the EMX need the accessory interface box?

For normal PC bench testing, yes. The LiDAR side uses 1000BASE-T1 vehicle Ethernet, while the interface box provides RJ45 Gigabit Ethernet for the host computer.

#### Why do the range and FOV values differ between sources?

The user guide lists 200 m range and 120 deg horizontal FOV, while the OpenELAB product listing mentions 300 m range and 140 deg horizontal FOV. Confirm the exact hardware revision, firmware, and sales specification before using those values in a design requirement.

#### Can RSView record data?

Yes. RSView can display real-time point clouds, record PCAP data, replay PCAP files, export CSV, and export LAS in RSView 3.1.3 or later.

#### What should I check if RSView shows no point cloud?

First verify packets in Wireshark. Then check firewall rules, the PC static IP, RSView sensor settings, MSOP/DIFOP ports, and whether the RSView path contains Chinese characters.

#### Is CAD available for the EMX?

Public CAD drawings were not confirmed during this review. Request a final mechanical drawing or CAD package before production bracket design.

#### Does this page include contact email or official support text?

No. This page intentionally omits support email, phone, and contact blocks while keeping engineering setup information.

### Source Notes

* Review date: 2026-06-02.
* Primary technical source: `RS-EMX_UserGuide_V1.0.8_EN.pdf`, version V1.0.8, dated 2025-08-07.
* Product listing source: OpenELAB Shopify product data checked on 2026-06-02.
* External links above were checked before draft upload.
* This is an engineering guide for integration and validation, not a final procurement datasheet. Confirm final public specifications, firmware behavior, CAD, and any compliance requirements before production use.
