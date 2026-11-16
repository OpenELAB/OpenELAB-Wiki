# RoboSense EM4 Thousand Beam Long Range Digital LiDAR Engineering Guide

Product link: https://openelab.io/products/robosense-em4-thousand-beam-long-range-digital-lidar?variant=45524593705158

![RoboSense EM4 product image](<../../.gitbook/assets/robosense em4 product.png>)

RoboSense EM4 is a long-range digital automotive LiDAR in RoboSense's EM platform. The OpenELAB listing describes the product as a thousand-beam long-range digital LiDAR for L3+ autonomous driving and ADAS development, with up to 1080 beams, up to 600 m maximum detection range, and 25.92 million points per second. The EM4 user manual available locally describes an EM4-B0 prototype with 300 m range at 10 percent NIST reflectivity, 120 deg horizontal FOV, 25 deg vertical FOV, 1000Base-T1 Ethernet output, UDP MSOP/DIFOP data, and gPTP synchronization support. Treat the listing and manual values as revision-dependent until the final hardware revision is confirmed.

## Overview

RoboSense EM4 is intended for long-range 3D perception in automotive and robotics development. The OpenELAB product page positions EM4 as a digital LiDAR with SPAD-SoC architecture, VCSEL-based emission, lossless point-cloud compression, high-definition 3D perception, and compatibility with in-vehicle Ethernet systems.

For engineering integration, the most important confirmed manual-level details are the Ethernet data path, fixed default network configuration, MSOP/DIFOP UDP packet outputs, interface-box connection method, and RSView/Wireshark workflow for first bring-up.

## Product And Variant Information

| Item                    | Value                                                  |
| ----------------------- | ------------------------------------------------------ |
| Product name            | RoboSense EM4 Thousand-Beam Long-Range Digital LiDAR   |
| Brand / manufacturer    | RoboSense / Suteng Innovation Technology Co., Ltd.     |
| OpenELAB vendor         | RoboSense                                              |
| Product handle          | `robosense-em4-thousand-beam-long-range-digital-lidar` |
| Selected variant ID     | `45524593705158`                                       |
| Selected variant        | `Robosense-EM4`                                        |
| Selected SKU            | `Robosense-EM4`                                        |
| OpenELAB product status | Available at time of review                            |

## Key Features

| Feature            | OpenELAB listing                           | EM4 user manual notes                                                      |
| ------------------ | ------------------------------------------ | -------------------------------------------------------------------------- |
| LiDAR class        | Thousand-beam long-range digital LiDAR     | High-performance automotive-grade LiDAR                                    |
| Maximum beams      | Up to 1080 beams                           | Manual does not use the same beam-count framing                            |
| Maximum range      | Up to 600 m maximum reach                  | 300 m at 10 percent NIST, 100 klux for EM4-B0 prototype                    |
| Field of view      | 120 deg x 27 deg listed                    | 120 deg horizontal, 25 deg vertical                                        |
| Angular resolution | 0.050 deg x 0.025 deg listed               | About 0.1 deg horizontal and about 0.05 deg vertical                       |
| Point rate         | 25.92 million pts/s listed                 | 6,240,000 pts/s single return mode                                         |
| Architecture       | SPAD-SoC digital architecture, VCSEL chips | Ethernet/UDP output with 3D coordinates, reflectivity, timestamps          |
| Compression        | Up to 60 percent compression ratio listed  | Manual emphasizes Ethernet output and UDP packets, not this listing metric |

## Specifications

The table below favors user-manual values for integration planning and keeps listing-only values separate.

| Category                      | Specification                                              |
| ----------------------------- | ---------------------------------------------------------- |
| Measurement range             | 300 m at 10 percent NIST, 100 klux, from EM4 user manual   |
| Listing maximum reach         | Up to 600 m, from OpenELAB product page                    |
| Typical accuracy              | +/-5 cm at 1 sigma                                         |
| Horizontal FOV                | 120 deg, -60 deg to +60 deg                                |
| Vertical FOV                  | 25 deg, -12.5 deg to +12.5 deg                             |
| Listing FOV                   | 120 deg x 27 deg                                           |
| Horizontal angular resolution | About 0.1 deg in user manual                               |
| Vertical angular resolution   | About 0.05 deg in user manual                              |
| Listing angular resolution    | 0.050 deg x 0.025 deg                                      |
| Output point rate             | 6,240,000 pts/s single return mode in user manual          |
| Listing point rate            | 25.92 million pts/s                                        |
| Ethernet output               | 1000Base-T1                                                |
| Communication protocol        | UDP                                                        |
| Data content                  | 3D spatial coordinates, reflectivity, timestamps           |
| Supply voltage                | 12 V nominal, 9 V to 16 VDC                                |
| Typical power                 | 16 W                                                       |
| Dimensions                    | 150 mm depth x 119 mm width x 45 mm height for B prototype |
| Weight                        | Less than 1000 g                                           |
| Operating temperature         | -40 C to +85 C                                             |
| Storage temperature           | -40 C to +105 C                                            |
| Time synchronization          | gPTP                                                       |
| Protection level              | IP67 / IP6K9K                                              |
| Frame rate                    | 10 Hz                                                      |
| Blind zone                    | 1 m                                                        |

## Hardware Architecture

The OpenELAB product page describes EM4 as a digital LiDAR built around SPAD-SoC architecture and VCSEL emission. It also highlights all-condition optical signal processing, crosstalk elimination, high-reflection blooming suppression, noise reduction in rain/fog/dust, and real-time lossless compression.

The EM4 user manual describes the integration path more concretely:

| Subsystem                         | Engineering role                                                                  |
| --------------------------------- | --------------------------------------------------------------------------------- |
| EM4 LiDAR body                    | Scans the environment and outputs 3D coordinates, reflectivity, and timestamps    |
| Automotive Ethernet power harness | Carries Ethernet and power between the LiDAR and interface box                    |
| Interface box                     | Converts or exposes the connection path for power and host Ethernet access        |
| Host computer                     | Receives UDP packets, runs RSView, Wireshark, tcpdump, SDK, ROS, or ROS 2 tools   |
| Time synchronization path         | gPTP-based synchronization when the related module and system support are present |

## Wiring And Interface

According to the EM4 user manual, EM4 uses an automotive Ethernet and power two-in-one connector. For lab bring-up, the manual describes connecting EM4 to an interface box through the vehicle Ethernet power harness, then connecting the interface box to the host PC through a Gigabit Industrial Ethernet RJ45 port.

| Interface                         | Manual description                            | Notes                                   |
| --------------------------------- | --------------------------------------------- | --------------------------------------- |
| Automotive Ethernet power harness | Combined Ethernet and power connection to EM4 | Used between LiDAR and interface box    |
| J1                                | Power wake-up signal                          | Provides power/wake-up related function |
| J2                                | Network                                       | 1000Base-T1 automotive Ethernet         |
| J3                                | DC power connector                            | External power input                    |
| J5                                | RJ45 Ethernet                                 | 1000Base-TX industrial Ethernet         |

The interface box only supports Gigabit Ethernet. Use a compatible Gigabit Ethernet adapter or port on the host side.

## Default Network Settings

| Device                 | IP address      | Port / role                                       |
| ---------------------- | --------------- | ------------------------------------------------- |
| EM4 LiDAR              | `192.168.1.200` | Source device IP in factory default configuration |
| Host computer example  | `192.168.1.102` | Configure PC to the same subnet                   |
| Subnet mask            | `255.255.255.0` | Typical manual example                            |
| MSOP destination port  | `6699`          | Point cloud / scan data output                    |
| DIFOP destination port | `7788`          | Device information output                         |

If the current device IP is unknown, connect the LiDAR and capture ARP packets with Wireshark. The manual example identifies the LiDAR source as `192.168.1.200` and the requested PC address as `192.168.1.102`.

Important integration note: EM4 uses a static ARP list and sends ARP packets only after the radar is powered on and before host communication is established. If the host computer is changed after normal communication, power-cycle the LiDAR so it can communicate with the new host.

## Software And Setup Workflow

{% stepper %}
{% step %}
## Connect the EM4 LiDAR to the interface box

Connect the EM4 LiDAR to the interface box through the automotive Ethernet power harness.
{% endstep %}

{% step %}
## Connect the interface box to the host PC

Connect the interface box RJ45 port to the host PC using Gigabit Ethernet.
{% endstep %}

{% step %}
## Power the system

Power the system and confirm the interface box indicator state described in the manual.
{% endstep %}

{% step %}
## Configure the host PC

Configure the host PC with a static IP on the same subnet, such as `192.168.1.102` with subnet mask `255.255.255.0`.
{% endstep %}

{% step %}
## Check network traffic

Use Wireshark or tcpdump to confirm ARP and UDP traffic.
{% endstep %}

{% step %}
## Open RSView

Open RSView to visualize point cloud data from the live Ethernet stream.
{% endstep %}

{% step %}
## Save a PCAP capture

Save a PCAP capture for repeatable debugging and offline replay.
{% endstep %}

{% step %}
## Configure SDK, ROS, or ROS 2

If using SDK, ROS, or ROS 2, configure the driver with the device IP, MSOP port, DIFOP port, and host network interface.
{% endstep %}
{% endstepper %}

RSView supports live display, PCAP recording, PCAP replay, custom coloring by distance/time/angle/beam, table view, CSV export, distance measurement, multi-frame playback, channel show/hide, and crop display. The manual states RSView supports Windows 64-bit and Ubuntu 18.04 or higher. Avoid Chinese characters in the extraction path.

## Communication Protocol

EM4 communicates over Ethernet using UDP. The manual defines two output packet types:

| Protocol | Function                            | Transport | Packet size | Send interval / rate |
| -------- | ----------------------------------- | --------- | ----------- | -------------------- |
| MSOP     | Main data stream / scan data output | UDP       | 1084 bytes  | 24,000 times/s       |
| DIFOP    | Product information output          | UDP       | 1310 bytes  | 10 times/s           |

MSOP packets encapsulate scanned distance, angle, reflectivity, and related point-cloud information. DIFOP packets are output-only and periodically report configuration, device status, and fault diagnosis information. The manual notes that DIFOP is divided into DIFOP1 with a 20 ms transmission cycle and DIFOP2 with a 2 s transmission cycle.

## Engineering Setup Checklist

| Check            | Expected result                                                                     |
| ---------------- | ----------------------------------------------------------------------------------- |
| Power input      | 12 V nominal, within 9 V to 16 VDC                                                  |
| Host Ethernet    | Gigabit-capable interface connected to interface box                                |
| Host static IP   | Same subnet as LiDAR, for example `192.168.1.102/24`                                |
| LiDAR IP         | Default `192.168.1.200` unless changed                                              |
| MSOP traffic     | UDP data observed on port `6699`                                                    |
| DIFOP traffic    | UDP data observed on port `7788`                                                    |
| RSView live view | Point cloud appears in real-time display                                            |
| PCAP capture     | Wireshark/tcpdump capture can be replayed or inspected                              |
| Revision check   | Confirm whether the hardware is EM4-B0 prototype or production EM4 listing revision |

## Best Practices And Limitations

* Use the user manual values for wiring, network, packet sizes, and first bring-up unless a newer official manual is provided.
* Treat OpenELAB listing values such as 1080 beams, 600 m maximum reach, 25.92 million pts/s, and 120 deg x 27 deg FOV as listing-level specifications that may apply to a different revision or operating mode than the EM4-B0 user manual.
* Confirm the final hardware revision, firmware version, and return/output mode before using the LiDAR in production design.
* Range, precision, power, and temperature behavior can vary with ambient temperature, target reflectivity, light intensity, airflow, and target distance.
* Power-cycle the LiDAR when changing host computers because of the static ARP behavior described in the manual.
* gPTP-related hardware or system support may not be included as a factory-standard feature in every setup.

## Troubleshooting

| Symptom                                      | Likely cause                                           | What to check                                                                       |
| -------------------------------------------- | ------------------------------------------------------ | ----------------------------------------------------------------------------------- |
| No point cloud in RSView                     | Host IP not on same subnet or wrong interface selected | Set PC to `192.168.1.102/24`, choose the correct Ethernet interface                 |
| Wireshark sees no ARP or UDP traffic         | Power, harness, interface box, or Ethernet link issue  | Check DC power, harness seating, interface box indicator, and Gigabit Ethernet link |
| LiDAR worked with one PC but not another     | Static ARP behavior                                    | Power-cycle EM4 after changing host computer                                        |
| MSOP visible but no device status            | DIFOP port/filter mismatch                             | Inspect UDP port `7788` and driver DIFOP settings                                   |
| Driver receives packets but data looks wrong | Manual/listing revision mismatch or wrong parser       | Confirm packet size: MSOP 1084 bytes and DIFOP 1310 bytes for this manual revision  |
| Time synchronization not locked              | gPTP module or network support absent                  | Verify gPTP-capable network path and whether the required module is included        |

## Project References And Application Ideas

* Long-range obstacle detection and highway-speed perception evaluation.
* Autonomous driving and ADAS sensor research using RSView, PCAP captures, and UDP packet analysis.
* ROS or ROS 2 point cloud integration with a fixed-IP Ethernet LiDAR.
* Sensor fusion experiments using EM4 point clouds with camera, radar, GNSS, and IMU systems.
* Bandwidth and compression evaluation for in-vehicle Ethernet perception pipelines.

## Resources

| Resource                 | Link                                                                                                     |
| ------------------------ | -------------------------------------------------------------------------------------------------------- |
| OpenELAB product page    | https://openelab.io/products/robosense-em4-thousand-beam-long-range-digital-lidar?variant=45524593705158 |
| RoboSense resources page | https://www.robosense.cn/resources                                                                       |
| Local manual source      | `RS-EM4_UserGuide_v1.1_EN.pdf`                                                                           |

## FAQ

<details>

<summary>What is the default IP address of RoboSense EM4?</summary>

The EM4 user manual lists the factory default device IP as `192.168.1.200`. The host PC example is `192.168.1.102` with subnet mask `255.255.255.0`.

</details>

<details>

<summary>Which ports does EM4 use for LiDAR data?</summary>

The manual lists MSOP point-cloud output on UDP port `6699` and DIFOP device-information output on UDP port `7788`.

</details>

<details>

<summary>What software can display EM4 point cloud data?</summary>

RoboSense RSView can display live Ethernet data, record PCAP files, replay PCAP captures, and export point-cloud data to CSV.

</details>

<details>

<summary>Does EM4 use USB?</summary>

No. The EM4 manual describes Ethernet communication over UDP through automotive Ethernet and an interface-box/RJ45 host connection. Do not use the AC1 USB workflow for EM4.

</details>

<details>

<summary>Why do OpenELAB and the manual show different performance values?</summary>

The OpenELAB listing describes the commercial "thousand-beam" EM4 positioning, including up to 1080 beams and up to 600 m reach. The available EM4 user manual describes an EM4-B0 prototype with 300 m range at 10 percent NIST and different point-rate/FOV details. Confirm the final hardware and firmware revision before production design.

</details>

<details>

<summary>What should I do if I change the host PC?</summary>

Power-cycle the LiDAR. The EM4 manual notes that EM4 uses a static ARP list and sends ARP packets only after power-on and before host communication.

</details>

## Source Notes

* Review date: 2026-06-04.
* OpenELAB product page checked: `RoboSense EM4 Thousand-Beam Long-Range Digital LiDAR`, selected variant `45524593705158`.
* Shopify endpoint checked: `https://openelab.io/products/robosense-em4-thousand-beam-long-range-digital-lidar.js`.
* Manual source: `RS-EM4_UserGuide_v1.1_EN.pdf`, manual version V1.1.0, revision dated 2025-05-15.
* Source conflict: the product listing and manual differ on beam count, maximum range, FOV, angular resolution, and point rate. Confirm final production hardware revision before publishing as a production-ready wiki page.
