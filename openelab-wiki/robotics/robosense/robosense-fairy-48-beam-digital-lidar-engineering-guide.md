# RoboSense Fairy 48 Beam Digital LiDAR Engineering Guide

{% hint style="info" %}
[**View RoboSense Fairy 48 Beam Digital LiDAR on OpenELAB**](https://openelab.io/products/robosense-fairy-mid-range-lidar)

**Product/variant:** RoboSense Fairy 48 Beam Digital LiDAR · **OpenELAB SKU:** `RS-Fairy48`
{% endhint %}

Product link: https://openelab.io/products/robosense-fairy-mid-range-lidar

![RoboSense Fairy product image](<../../.gitbook/assets/robosense fairy product.jpg>)

RoboSense Fairy is a compact 48-channel digital LiDAR for medium-range 3D perception. This OpenELAB wiki guide summarizes the Fairy user manual and OpenELAB product listing for engineers who need to bring up the sensor, configure networking, use the Web UI and RSView, and parse MSOP/DIFOP UDP packets. Fairy provides 360 deg horizontal coverage, about 32 deg vertical coverage, up to 150 m range, multiple return modes, GPS/PTP/gPTP time synchronization options, and a factory default Ethernet configuration of `192.168.1.200` with MSOP on `6699` and DIFOP on `7788`.

## Overview

Fairy is designed for high-density 360-degree point-cloud sensing in robotics, mapping, perception research, and autonomous systems. The manual describes a chip-based digital LiDAR architecture with reflectivity output, phase lock, Web UI configuration, RSView visualization, and ROS/ROS 2 package references.

## Product And Variant Information

| Item                 | Value                                                                      |
| -------------------- | -------------------------------------------------------------------------- |
| Product name         | Robosense Fairy Mid-range Digital LiDAR 48 Beams High-Res 360 deg x 32 deg |
| Brand / manufacturer | RoboSense / Suteng Innovation Technology Co., Ltd.                         |
| OpenELAB vendor      | RoboSense                                                                  |
| OpenELAB handle      | `robosense-fairy-mid-range-lidar`                                          |
| Variant              | Only LiDAR, Accessory-Kit, LiDAR with Accessory Kit                        |
| SKU examples         | `RS-Fairy48`, `RS-Fairy48-Accessory`, `RS-Fairy48-Kit`                     |
| Manual title         | RS-LiDAR-Fairy User Guide                                                  |
| Manual version       | 1.0                                                                        |
| Manual revision date | 2026-02-01                                                                 |

## Specifications

| Category                      | Specification                                                        |
| ----------------------------- | -------------------------------------------------------------------- |
| Channels                      | 48                                                                   |
| Horizontal FOV                | 0 to 360 deg                                                         |
| Vertical FOV                  | -15.84 deg to +15.84 deg                                             |
| Laser safety                  | Class 1 eye safe                                                     |
| Measurement range             | 150 m, including 80 m at 10 percent NIST                             |
| Blind zone                    | <=0.2 m                                                              |
| Horizontal angular resolution | 0.25 deg                                                             |
| Vertical angular resolution   | 0.67 deg                                                             |
| Rotation speed                | 600 rpm                                                              |
| Typical precision             | 0.5 cm at 1 sigma                                                    |
| Output points                 | About 690,000 pts/s single return; about 1,380,000 pts/s dual return |
| Frame rate                    | 10 Hz                                                                |
| Ethernet bandwidth            | <19 Mbps                                                             |
| Output protocol               | UDP packets over Ethernet                                            |
| Data content                  | Spatial coordinates, reflectivity, timestamp                         |
| Operating voltage             | 9 V to 32 V                                                          |
| Power consumption             | <10 W                                                                |
| Dimensions                    | Diameter 75 mm x height 70 mm                                        |
| Body weight                   | <350 g                                                               |
| Operating temperature         | -40 C to +60 C                                                       |
| Storage temperature           | -40 C to +85 C                                                       |
| Time synchronization          | GPS, PTP, gPTP                                                       |
| Protection level              | IP67 / IP6K9K                                                        |

## Hardware Architecture

| Subsystem                | Engineering role                                                                             |
| ------------------------ | -------------------------------------------------------------------------------------------- |
| 48-channel LiDAR head    | Generates 360-degree point cloud and reflectivity data                                       |
| Aviation plug            | Main sensor connection for power, Ethernet, and synchronization                              |
| Optional interface cable | Breaks out power, RJ45 Ethernet, and synchronization interfaces                              |
| Host computer            | Receives UDP point cloud/device data and runs RSView, Wireshark, tcpdump, SDK, ROS, or ROS 2 |
| Web UI                   | Used for parameter settings, operational information, status checks, and firmware upgrades   |

## Field Of View And Return Modes

Fairy provides full 360-degree horizontal coverage and about 32-degree vertical coverage. The manual notes that the design architecture and scanning sequence can cause approximately 6 ms of point cloud unavailability per second; about one out of every 10 frames can have a gap of about 30 deg. The starting angle of the gap can be configured in firmware, so set it to a less critical region for the application.

| Return mode      | DIFOP flag at byte offset 300 |
| ---------------- | ----------------------------- |
| Strongest return | `0x00`                        |
| First return     | `0x01`                        |
| Last return      | `0x02`                        |
| Dual return      | `0x03`                        |

Dual return mode can detect two returns when targets are separated by more than 1 m.

## Wiring And Interface

Fairy connects through an aviation plug and optional interface cable. The optional cable can expose power, RJ45 Ethernet, and synchronization interfaces. Time synchronization modules such as GPS, PTP, and gPTP may require optional hardware or configuration.

| Interface            | Notes                                                                |
| -------------------- | -------------------------------------------------------------------- |
| Power                | 9 V to 32 V operating voltage                                        |
| RJ45 Ethernet        | Host data connection for UDP packets                                 |
| GPS sync             | RS232-level GPS timing interface described in the manual             |
| PTP/gPTP             | Configurable through Web UI when supported by the system             |
| Optional accessories | Aviation connector cable, power adapter, power cable, Ethernet cable |

## Default Network Settings

| Device                 | IP address      | Port / role                   |
| ---------------------- | --------------- | ----------------------------- |
| Fairy LiDAR            | `192.168.1.200` | Factory default device IP     |
| Host computer example  | `192.168.1.102` | Configure host to same subnet |
| Subnet mask            | `255.255.255.0` | Manual example                |
| MSOP destination port  | `6699`          | Point cloud data              |
| DIFOP destination port | `7788`          | Device information            |

If the current device IP is unknown, capture ARP packets in Wireshark after connecting and powering the LiDAR. The manual example shows the LiDAR source IP as `192.168.1.200` and the requested PC IP as `192.168.1.102`.

## Software And Setup Workflow

1. Connect Fairy through the aviation plug and optional cable assembly.
2. Connect the host PC to the RJ45 Ethernet interface.
3. Power on the LiDAR.
4. Configure the host PC to the same subnet, for example `192.168.1.102/24`.
5. Use Wireshark or tcpdump to confirm ARP and UDP traffic.
6. Open the Web UI at `http://192.168.1.200` unless the device IP has been changed.
7. Use RSView for live point-cloud visualization, PCAP recording, replay, table view, CSV export, and LAS export in RSView 3.1.3 or later.
8. For ROS/ROS 2 integration, confirm package version, packet type, return mode, and firmware compatibility.

## Communication Protocol

Fairy uses Ethernet and UDP. The manual defines two output protocols:

| Protocol | Function                              | Transport | Packet size | Send interval   |
| -------- | ------------------------------------- | --------- | ----------- | --------------- |
| MSOP     | Main data stream / point cloud output | UDP       | 1248 bytes  | About 555.55 us |
| DIFOP    | Device information output             | UDP       | 1248 bytes  | About 1 s       |

MSOP packets contain laser scan data such as distance, angle, reflectivity, and timing. DIFOP packets output configuration and current state information. Reflectivity uses RoboSense's proprietary scale from 1 to 255.

## Engineering Setup Checklist

| Check         | Expected result                                      |
| ------------- | ---------------------------------------------------- |
| Power input   | 9 V to 32 V supply available                         |
| Host IP       | Same subnet as LiDAR, for example `192.168.1.102/24` |
| LiDAR IP      | Default `192.168.1.200` unless changed               |
| Web UI        | Browser reaches the device IP                        |
| MSOP traffic  | UDP data observed on port `6699`                     |
| DIFOP traffic | UDP data observed on port `7788`                     |
| RSView        | Live point cloud appears                             |
| Return mode   | Strongest/first/last/dual configured as needed       |
| Time sync     | GPS/PTP/gPTP mode selected and validated if required |

## Best Practices And Limitations

* Confirm the final hardware, firmware, and return-mode configuration before production use.
* Account for the documented 30-degree point-cloud gap behavior when planning sensor placement.
* Range, precision, power, and thermal behavior depend on target reflectivity, distance, ambient light, and airflow.
* Use PCAP captures as a regression artifact before writing or changing parsers.
* Do not assume optional time-sync accessories are included; verify the purchased kit.

## Troubleshooting

| Symptom                         | Likely cause                                            | What to check                                                        |
| ------------------------------- | ------------------------------------------------------- | -------------------------------------------------------------------- |
| No point cloud in RSView        | Host IP, firewall, or wrong network interface           | Configure host IP, allow RSView through firewall, select correct NIC |
| Web UI does not open            | Wrong device IP or subnet                               | Check ARP packets and verify host IP/subnet                          |
| MSOP present but no DIFOP       | Port/filter mismatch                                    | Inspect UDP port `7788`                                              |
| Timing not locked               | GPS/PTP/gPTP not configured or unsupported network path | Verify Web UI mode, cable/module, and time source                    |
| Point cloud has a recurring gap | Known scanning architecture behavior                    | Configure gap starting angle in firmware if supported                |

## Project References And Application Ideas

* 360-degree mapping and obstacle detection for robots.
* Mid-range point-cloud datasets for perception algorithms.
* Web UI and RSView-based sensor validation workflows.
* ROS/ROS 2 point-cloud integration with fixed-IP UDP LiDAR data.
* Return-mode comparison for vegetation, reflective targets, or multi-surface scenes.

## Resources

| Resource                 | Link                                                                                        |
| ------------------------ | ------------------------------------------------------------------------------------------- |
| OpenELAB product page    | https://openelab.io/products/robosense-fairy-mid-range-lidar                                |
| RoboSense resources page | https://www.robosense.ai/en/resources                                                       |
| Local manual source      | `Fairy_EN_48TX_V1.0.pdf`                                                                    |
| Structural drawings      | Referenced in manual appendix; verify latest official drawing before mechanical integration |
| ROS / ROS 2 package      | Referenced in manual appendix; confirm current package from official RoboSense resources    |

## FAQ

<details>

<summary>What is the default IP address of RoboSense Fairy?</summary>

The manual lists `192.168.1.200` as the default LiDAR IP. The host PC example is `192.168.1.102` with subnet mask `255.255.255.0`.

</details>

<details>

<summary>Which UDP ports does Fairy use?</summary>

Fairy uses MSOP on port `6699` for point cloud data and DIFOP on port `7788` for device information.

</details>

<details>

<summary>Does Fairy have a Web UI?</summary>

Yes. The Web UI is available at the device IP, default `http://192.168.1.200`, and supports settings, status viewing, and firmware-related operations.

</details>

<details>

<summary>What is the Fairy point-cloud gap note?</summary>

The manual states that approximately 6 ms of point cloud data per second can be unavailable, and about one out of every 10 frames can contain a gap of about 30 deg. The starting angle can be configured in firmware.

</details>

## Source Notes

* Review date: 2026-06-04.
* Product source: OpenELAB product page and Shopify endpoint for `robosense-fairy-mid-range-lidar`.
* Manual source: `Fairy_EN_48TX_V1.0.pdf`, manual version 1.0, revision dated 2026-02-01.
* Outbound link check: OpenELAB product page and RoboSense resources page were reachable during review.
* Excluded from this wiki: manufacturer email, phone, address, working hours, and support contact blocks from the source manual.
