# RoboSense EM4 User Manual Engineering Guide

Product link: https://openelab.io/products/robosense-em4-thousand-beam-long-range-digital-lidar

![RoboSense EM4 product image](<../../.gitbook/assets/robosense em4 product (1).png>)

RoboSense EM4 is a high-performance automotive-grade LiDAR. This OpenELAB wiki page is a manual-focused engineering guide based on `RS-EM4_UserGuide_v1.1_EN.pdf`, separate from the existing OpenELAB product-listing guide. It focuses on EM4-B0 prototype manual details: 300 m range at 10 percent NIST and 100 klux, 120 deg x 25 deg FOV, 1000Base-T1 Ethernet output, interface-box wiring, default IP and UDP ports, RSView usage, MSOP/DIFOP packet sizes, gPTP synchronization, and static ARP behavior.

## Overview

The EM4 manual describes the status and functions of the EM4-B0 prototype. Use this page as a practical bring-up and protocol reference, not as a replacement for the latest production datasheet. The OpenELAB product listing includes additional commercial positioning such as thousand-beam operation and longer maximum-reach claims, so confirm final hardware and firmware revision before using any value for production design.

## Product And Variant Information

| Item                 | Value                                                                                         |
| -------------------- | --------------------------------------------------------------------------------------------- |
| Product name         | RoboSense EM4 Thousand-Beam Long-Range Digital LiDAR                                          |
| Brand / manufacturer | RoboSense / Suteng Innovation Technology Co., Ltd.                                            |
| OpenELAB vendor      | RoboSense                                                                                     |
| OpenELAB handle      | `robosense-em4-thousand-beam-long-range-digital-lidar`                                        |
| Variant examples     | `Robosense-EM4`, `0.5m Accessory Set`, `3.5m Accessory Set`, LiDAR with Ethernet kit          |
| SKU examples         | `Robosense-EM4`, `Robosense-EM4-0.5m`, `Robosense-EM4-3.5m`, `RS-EM4-0.5Kit`, `RS-EM4-3.5Kit` |
| Manual title         | EM4 User Manual                                                                               |
| Manual version       | V1.1.0                                                                                        |
| Manual revision date | 2025-05-15                                                                                    |

## Specifications

| Category                      | Specification                                              |
| ----------------------------- | ---------------------------------------------------------- |
| Measurement range             | 300 m at 10 percent NIST, 100 klux                         |
| Typical accuracy              | +/-5 cm at 1 sigma                                         |
| Horizontal FOV                | 120 deg, -60 deg to +60 deg                                |
| Vertical FOV                  | 25 deg, -12.5 deg to +12.5 deg                             |
| Horizontal angular resolution | About 0.1 deg                                              |
| Vertical angular resolution   | About 0.05 deg                                             |
| Output point rate             | 6,240,000 pts/s single return mode                         |
| Ethernet output               | 1000Base-T1                                                |
| Communication protocol        | UDP                                                        |
| Data content                  | 3D spatial coordinates, reflectivity, timestamps           |
| Supply voltage                | 12 V nominal, 9 V to 16 VDC                                |
| Typical power                 | 16 W                                                       |
| Dimensions                    | 150 mm depth x 119 mm width x 45 mm height for B prototype |
| Weight                        | <1000 g                                                    |
| Operating temperature         | -40 C to +85 C                                             |
| Storage temperature           | -40 C to +105 C                                            |
| Time synchronization          | gPTP                                                       |
| Protection level              | IP67 / IP6K9K                                              |
| Frame rate                    | 10 Hz                                                      |
| Blind zone                    | 1 m                                                        |

## Hardware Architecture

| Subsystem                         | Engineering role                                                                          |
| --------------------------------- | ----------------------------------------------------------------------------------------- |
| EM4 LiDAR                         | Scans the environment and outputs 3D coordinates, reflectivity, and timestamps            |
| Automotive Ethernet power harness | Combines Ethernet and power path to the sensor                                            |
| Interface box                     | Provides power wake-up, 1000Base-T1 automotive Ethernet, DC input, and RJ45 host Ethernet |
| Host computer                     | Receives UDP packets and runs RSView, Wireshark, tcpdump, SDK, ROS, or ROS 2              |
| gPTP timing path                  | Supports time synchronization when the system and module support it                       |

## Wiring And Interface

The EM4 manual describes an automotive Ethernet and power two-in-one connector. For lab bring-up, connect EM4 to the interface box through the vehicle Ethernet power harness, then connect the interface box to the host PC using Gigabit Industrial Ethernet through RJ45.

| Interface | Manual description                                            |
| --------- | ------------------------------------------------------------- |
| J1        | Power wake-up signal; provides power/wake-up related function |
| J2        | Network; 1000Base-T1 automotive Ethernet                      |
| J3        | DC power connector; external power input                      |
| J5        | RJ45 Ethernet; 1000Base-TX industrial Ethernet                |

The interface box only supports Gigabit Ethernet. Use a compatible host NIC and avoid Fast Ethernet adapters.

## Default Network Settings

| Device                 | IP address      | Port / role                   |
| ---------------------- | --------------- | ----------------------------- |
| EM4 LiDAR              | `192.168.1.200` | Factory default device IP     |
| Host computer example  | `192.168.1.102` | Configure host to same subnet |
| Subnet mask            | `255.255.255.0` | Manual example                |
| MSOP destination port  | `6699`          | Scan / point cloud output     |
| DIFOP destination port | `7788`          | Product information output    |

> Important: the manual states that EM4 uses a static ARP list and sends ARP packets only after power-on and before host communication is established. If the host computer is replaced after normal communication, power-cycle EM4 before trying to communicate with the new host.

## Software And Setup Workflow

1. Connect EM4 to the interface box through the automotive Ethernet power harness.
2. Connect the PC to the interface box using Gigabit Ethernet through RJ45.
3. Power the system and confirm the interface box indicator state.
4. Configure the PC to `192.168.1.102` with subnet mask `255.255.255.0`, unless the device configuration has changed.
5. Use Wireshark to inspect ARP packets and confirm the LiDAR source IP.
6. Use RSView for live point-cloud display and PCAP recording/replay.
7. Confirm MSOP and DIFOP packet sizes before writing custom parsers.
8. For ROS/ROS 2 or SDK integration, pin firmware, packet format, return mode, and host network settings in the project documentation.

RSView supports live display, PCAP save/replay, custom coloring, point table view, CSV export, distance measurement, multi-frame playback, channel show/hide, and crop display. The manual lists Windows 64-bit and Ubuntu 18.04 or later support.

## Communication Protocol

EM4 communicates over Ethernet using UDP. The manual defines:

| Protocol | Function                            | Transport | Packet size | Rate           |
| -------- | ----------------------------------- | --------- | ----------- | -------------- |
| MSOP     | Main data stream / scan data output | UDP       | 1084 bytes  | 24,000 times/s |
| DIFOP    | Product information output          | UDP       | 1310 bytes  | 10 times/s     |

MSOP packets encapsulate scanned distance, angle, reflectivity, and related point-cloud information. DIFOP is output-only and periodically reports configuration, device status, and fault diagnosis information. The manual states that DIFOP is divided into DIFOP1 with a 20 ms transmission cycle and DIFOP2 with a 2 s transmission cycle.

## Engineering Setup Checklist

| Check            | Expected result                                               |
| ---------------- | ------------------------------------------------------------- |
| Power            | 12 V nominal, within 9 V to 16 VDC                            |
| Host Ethernet    | Gigabit-capable interface connected to interface box          |
| Host static IP   | Same subnet as LiDAR, for example `192.168.1.102/24`          |
| LiDAR IP         | Default `192.168.1.200` unless changed                        |
| MSOP traffic     | UDP packets on port `6699`                                    |
| DIFOP traffic    | UDP packets on port `7788`                                    |
| RSView live view | Point cloud appears                                           |
| Packet parser    | MSOP 1084 bytes and DIFOP 1310 bytes for this manual revision |
| ARP behavior     | Power-cycle sensor after changing host computer               |

## Best Practices And Limitations

* Treat the manual as an EM4-B0 prototype reference and confirm production revision data separately.
* Range, accuracy, power, and temperature behavior depend on target reflectivity, ambient light, airflow, and target distance.
* Use Wireshark or tcpdump PCAP captures as integration evidence before deploying software changes.
* Confirm gPTP support in the complete system; the timing module may not be included in every setup.
* Do not mix EM4 packet sizes with Fairy or other RoboSense LiDAR packet definitions.

## Troubleshooting

| Symptom                              | Likely cause                                     | What to check                                                                   |
| ------------------------------------ | ------------------------------------------------ | ------------------------------------------------------------------------------- |
| RSView does not display point clouds | Firewall, wrong NIC, wrong IP, or packet setting | Allow RSView through firewall, select correct NIC, verify host IP and MSOP port |
| No ARP or UDP traffic                | Power, harness, interface box, or link issue     | Check power, harness seating, interface box indicator, Gigabit link             |
| Works on one PC but not another      | Static ARP behavior                              | Power-cycle EM4 after changing host computer                                    |
| DIFOP missing                        | Port/filter mismatch                             | Inspect UDP port `7788`                                                         |
| Parser fails                         | Wrong manual revision or packet length           | Confirm MSOP 1084 bytes and DIFOP 1310 bytes                                    |
| Time sync not locked                 | gPTP path not configured or unsupported          | Verify gPTP-capable switch/host and module availability                         |

## Project References And Application Ideas

* Automotive-grade long-range LiDAR bring-up and validation.
* UDP packet parser development using MSOP/DIFOP captures.
* RSView + PCAP workflow for sensor acceptance testing.
* ROS/ROS 2 point-cloud driver validation.
* Sensor fusion with camera, radar, GNSS, and IMU pipelines.

## Resources

| Resource                 | Link                                                                                    |
| ------------------------ | --------------------------------------------------------------------------------------- |
| OpenELAB product page    | https://openelab.io/products/robosense-em4-thousand-beam-long-range-digital-lidar       |
| RoboSense resources page | https://www.robosense.cn/resources                                                      |
| Local manual source      | `RS-EM4_UserGuide_v1.1_EN.pdf`                                                          |
| Firmware package         | Not confirmed during this review                                                        |
| CAD / production drawing | Not confirmed during this review                                                        |
| ROS / ROS 2 package      | Referenced by the manual; confirm the current package from official RoboSense resources |

## FAQ

<details>

<summary>What is the default IP address of RoboSense EM4?</summary>

The manual lists the factory default EM4 IP as `192.168.1.200`. The host PC example is `192.168.1.102` with subnet mask `255.255.255.0`.

</details>

<details>

<summary>Which ports does EM4 use?</summary>

EM4 uses UDP port `6699` for MSOP scan data and UDP port `7788` for DIFOP product information.

</details>

<details>

<summary>Why does EM4 stop communicating after changing the host PC?</summary>

The manual states that EM4 uses a static ARP list and sends ARP packets only after power-on and before host communication. Power-cycle EM4 when switching host computers.

</details>

<details>

<summary>Is this page the same as the OpenELAB EM4 product guide?</summary>

No. This page is a manual-focused engineering guide for `RS-EM4_UserGuide_v1.1_EN.pdf`. The existing OpenELAB EM4 product guide also discusses product-listing specifications and source conflicts.

</details>

## Source Notes

* Review date: 2026-06-04.
* Product source: OpenELAB product page and Shopify endpoint for `robosense-em4-thousand-beam-long-range-digital-lidar`.
* Manual source: `RS-EM4_UserGuide_v1.1_EN.pdf`, manual version V1.1.0, revision dated 2025-05-15.
* Outbound link check: OpenELAB product page and RoboSense resources page were reachable during review.
* Excluded from this wiki: manufacturer email, phone, address, working hours, and support contact blocks from the source manual.
