---
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
[**View RoboSense M1 Plus 12 V LiDAR with accessory kit on OpenELAB**](https://openelab.io/products/robosense-m1-plus-solid-state-lidar)

**Model:** RS-LiDAR-M1P (M1 Plus) · **OpenELAB SKU:** `RS-M1P-12-Kit` · **Option:** 12 V LiDAR with accessory kit. **The separate 24 V configuration must not use 12 V electrical assumptions.**
{% endhint %}

## Product overview

RoboSense M1 Plus is a MEMS solid-state 3D LiDAR intended for environment perception, mapping and research involving automotive-style Ethernet. The purchased 12 V kit contains the sensor and an interface/power cable set. Unlike an ordinary RJ45 Ethernet sensor, the M1P uses **1000BASE-T1 automotive Ethernet** at its sensor connector; the matching interface box and cable assembly provide the supported connection path to a conventional computer.

This guide applies to the **M1 Plus (RS-LiDAR-M1P)**, not a generic RS-LiDAR-M1, and the 12 V OpenELAB kit option. RoboSense also sells 24 V versions and sensor-only packages. Verify the physical label and the supplied power/ethernet harness before installation. [Manufacturer product information](https://store.robosense.ai/products/m1-plus) · [OpenELAB kit contents](https://openelab.io/products/robosense-m1-plus-solid-state-lidar).

## Applications

* Obstacle and free-space perception for vehicle and autonomous navigation research
* 3D mapping, localization and multi-sensor data collection
* Roadside and transportation scene sensing prototypes

These are engineering integration examples, not claims that the LiDAR alone constitutes a certified functional-safety system.

## Key specifications

The following values are **from the RoboSense RS-LiDAR-M1P User Guide, revision 1.3.0 (21 December 2022)** and apply to its documented 12 V hardware. Confirm current unit revision and test conditions before making design or safety decisions.

| Parameter                 | Documented 12 V M1P value / conditions                                                                 |
| ------------------------- | ------------------------------------------------------------------------------------------------------ |
| Technology                | MEMS time-of-flight 3D LiDAR                                                                           |
| Horizontal / vertical FOV | 120° / 25° nominal                                                                                     |
| Range                     | 0.5–200 m; up to 180 m at 10% NIST target reflectivity                                                 |
| Range precision           | ±5 cm (1σ) under the manual's target and measurement conditions                                        |
| Frame rate                | 10 Hz in the referenced user guide                                                                     |
| Data output               | Approximately 750,000 points/s single return; 1.5 million points/s dual return in the referenced guide |
| Sensor data interface     | 1000BASE-T1 automotive Ethernet, UDP MSOP/DIFOP packets                                                |
| Power                     | 9–16 V DC for the **documented 12 V variant**; approximately 15 W in the stated test conditions        |
| Mechanical outline        | Approximately 110 × 111 × 45 mm; confirm against the drawing before CAD integration                    |
| Environmental rating      | IP67 / IP6K9K as specified in the manufacturer's guide                                                 |

**Revision warning:** The OpenELAB store lists newer point-rate and other specifications that differ slightly from the 2022 guide. Do not silently mix those numbers or use the 9–16 V range for the separate **24 V** variant. Use the actual unit's latest manufacturer datasheet where available.

## Hardware and connections

The 12 V accessory kit listing identifies a matched Ethernet/power cable, power adapter, power cable, E1R interface box, RJ45 cable and mounting fasteners. Verify the actual package contents. The original user's guide documents the **1000BASE-T1 sensor end and power/wakeup harness** and the interface box's Ethernet connection to a PC.

1. Check the LiDAR model, **12 V** marking and cable/interface-box part numbers. Do not substitute a 24 V supply based on another M1 Plus variant.
2. With all power removed, mount the sensor, check cable strain relief and follow the connector and pinout drawings in **RS-LiDAR-M1P User Guide, §3.1–3.2**. Do not connect a standard RJ45 plug directly to an automotive Ethernet mating connector.
3. Connect the interface box's normal RJ45 Ethernet port to the computer and use only the supplied/approved power path. Ensure the sensor has an unobstructed field of view and adequate ventilation.
4. Identify and document the host Ethernet adapter before changing its network settings.

For production mounting, use the manufacturer's dimensioned drawing in Appendix C, not dimensions reconstructed from photographs.

## Software and development resources

| Resource                | Supported use                                                                              | Link                                                                                                                                                                                                                                                                  |
| ----------------------- | ------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| RSView                  | Windows 64-bit live point-cloud visualization and PCAP capture                             | Installation and configuration in the [M1P User Guide, Appendix A](https://cdn.robotshop.com/media/U/UTR/RB-Utr-08/pdf/robosense-rs-lidar-m1-plus-advanced-2d-mems-smart-chip-lidar-200m-range-user-guide.pdf); obtain a compatible executable/release from RoboSense |
| RoboSense rs\_driver    | C++ LiDAR decoding and online/PCAP examples; confirm the matching M1P firmware and release | [Official driver repository and support matrix](https://github.com/RoboSense-LiDAR/rs_driver)                                                                                                                                                                         |
| RoboSense rslidar\_sdk  | ROS / ROS 2 publishing through rs\_driver                                                  | [Official ROS driver and setup instructions](https://github.com/RoboSense-LiDAR/rslidar_sdk)                                                                                                                                                                          |
| Manufacturer M1P manual | Power, wiring, packet definitions, RSView and mechanical drawings                          | [RS-LiDAR-M1P User Guide, revision 1.3.0 (PDF)](https://cdn.robotshop.com/media/U/UTR/RB-Utr-08/pdf/robosense-rs-lidar-m1-plus-advanced-2d-mems-smart-chip-lidar-200m-range-user-guide.pdf)                                                                           |

The current public rs\_driver README explicitly lists **RS-LiDAR-M1**, while the manufacturer's M1P guide uses the **RSM1** software selection. Verify exact M1 Plus firmware/packet compatibility with the intended driver version rather than assuming that every M1-labelled release is interchangeable.

## Getting started: capture the first point cloud

### Prerequisites

* The **M1 Plus 12 V kit** with its matching interface/power harness, a Windows 64-bit computer with wired Ethernet and a compatible manufacturer-supplied RSView application
* Permission to configure the host adapter and firewall, a controlled test environment, the manufacturer's user guide and hardware labels

### Connection, network and RSView

1. Follow the power-off connection procedure above. Using the factory unicast network configuration in **RS-LiDAR-M1P User Guide rev. 1.3.0**, configure the PC's dedicated wired Ethernet adapter to **192.168.1.102**, subnet mask **255.255.255.0**. The documented default LiDAR address is **192.168.1.200**. If the unit was previously reconfigured, verify its actual network settings rather than forcing the defaults.
2. Power the 12 V kit with the manufacturer-compatible adapter and interface box. Confirm the cable and interface-box indicators against the manufacturer instructions.
3. Open the manufacturer-compatible **RSView** application. Choose **File → Open Sensor**, select **RSM1** for M1P as specified in the cited revision of Appendix A, and review the displayed sensor calibration/connection settings.
4. Confirm **MSOP UDP port 6699** and **DIFOP UDP port 7788**, the factory default host target in the 2022 manual. Configure the current sensor port settings if they differ. Permit the application through the host firewall for this isolated test network.
5. Observe a live, changing 3D point cloud. For a repeatable diagnostic record, save a short PCAP capture and record the sensor revision, firmware, host IP, viewer version and port values.

**Expected result:** RSView receives and displays an updating colored point cloud. Capturing UDP packets without decoded points establishes connectivity but not correct driver/model compatibility.

**If this fails:** inspect supply/wakeup and interface-box state → cable/host link → computer IP/subnet → sensor's actual destination IP → firewall → UDP ports → RSView model/firmware compatibility. Refer to the guide's **Appendix A.3–A.4** before altering firmware.

## Troubleshooting and FAQs

| Symptom                                         | Ordered checks                                                                                                                                     |
| ----------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| No Ethernet traffic                             | Verify approved 12 V power, wakeup/interface-box connections and link indications; check the manufacturer's harness drawing                        |
| Packets arrive, but no point cloud              | Confirm the correct RSView **RSM1** profile, UDP 6699/7788 settings, current firmware and packet compatibility                                     |
| Point cloud freezes intermittently              | Check network interface and packet loss first, then power stability, cabling, cooling and viewer host capacity                                     |
| Unsure whether the power supply is 12 V or 24 V | Stop and confirm the **actual unit's label and exact kit variant**; do not use a generic M1P voltage value                                         |
| ROS 2 sees no points                            | First reproduce the live PCAP/RSView test; then select a verified M1/M1P-supported driver configuration and inspect the ROS 2 topic and timestamps |

## Downloads and technical documents

| Document                                                                                                                                                                    | Purpose                                                                               | Scope                                                                 |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| [RoboSense M1 Plus product listing](https://store.robosense.ai/products/m1-plus)                                                                                            | Model and option verification                                                         | Current manufacturer storefront; verify hardware option               |
| [RS-LiDAR-M1P User Guide (PDF)](https://cdn.robotshop.com/media/U/UTR/RB-Utr-08/pdf/robosense-rs-lidar-m1-plus-advanced-2d-mems-smart-chip-lidar-200m-range-user-guide.pdf) | Full electrical and interface diagrams, UDP protocol, RSView instructions, dimensions | Revision 1.3.0, dated 2022-12-21; OEM-authored and distributor-hosted |
| [RoboSense rs\_driver](https://github.com/RoboSense-LiDAR/rs_driver)                                                                                                        | C++ decoder, PCAP and online demos                                                    | Check release support matrix and build requirements                   |
| [RoboSense rslidar\_sdk](https://github.com/RoboSense-LiDAR/rslidar_sdk)                                                                                                    | ROS / ROS 2 packages and examples                                                     | Confirm model/firmware support before deployment                      |

### Existing OpenELAB file attachment

{% file src="../../.gitbook/assets/M1P_Certification.zip" %}

## References and validation

Sources reviewed on **18 November 2026**: [RoboSense manufacturer M1 Plus listing](https://store.robosense.ai/products/m1-plus); [RoboSense RS-LiDAR-M1P User Guide, v1.3.0](https://cdn.robotshop.com/media/U/UTR/RB-Utr-08/pdf/robosense-rs-lidar-m1-plus-advanced-2d-mems-smart-chip-lidar-200m-range-user-guide.pdf); [RoboSense rs\_driver](https://github.com/RoboSense-LiDAR/rs_driver); [RoboSense rslidar\_sdk](https://github.com/RoboSense-LiDAR/rslidar_sdk); and [OpenELAB SKU/kit listing](https://openelab.io/products/robosense-m1-plus-solid-state-lidar).

**Software execution:** not run. **Physical hardware test:** not run. **Remaining integration check:** confirm the latest exact-revision M1 Plus user guide and driver compatibility for the delivered serial number/firmware before production deployment.
