# Hesai JT128 3D LiDAR Engineering Guide

{% hint style="info" %}
[**View Hesai JT128 3D LiDAR on OpenELAB**](https://openelab.io/products/hesai-jt128-3d-lidar-avg)

**Product model/family:** Hesai JT128 3D LiDAR · **OpenELAB SKU:** `HESAI-JT128`
{% endhint %}

[Product link](https://openelab.io/products/hesai-jt128-3d-lidar-avg)

## Hesai JT128 3D LiDAR Engineering Guide

The Hesai JT128 is a compact 128-channel mechanical 3D LiDAR for AGV, AMR, robotics, mapping, obstacle perception, and autonomous navigation. It combines a small embedded-installation form factor with 360 degree horizontal coverage, high-density point clouds, dual-return operation up to 2,304,000 points/s, 100Base-TX Ethernet output, GNSS/PTP time synchronization, and IP6K7 ingress protection. This guide collects the practical engineering details needed to evaluate, mount, configure, and integrate the JT128 into robotics perception stacks.

### Quick Summary

* **Product:** Hesai JT128, OpenELAB SKU HESAI-JT128.
* **Best fit:** AMR/AGV navigation, robotics mapping, autonomous lawn/farming robots, service robots, smart logistics robots, and high-density near-field 3D perception.
* **Perception profile:** 128 channels, mechanical rotation, 360 degree horizontal field of view, 40 m ranging capability at 10 percent reflectivity, and 60 m instrumented range.
* **Software ecosystem:** PandarView 2 visualization, LidarUtilities, HesaiLidar SDK 2.0, and HesaiLidar ROS 2.0 for ROS/ROS2 point cloud publishing.
* **Category:** Sensors / LiDAR / Robotics perception.

### FOV Note: Product Page vs Manual

{% hint style="info" %}
Hesai markets the JT128/64P series as a mini 360 x 189 degree hyper-hemispherical 3D LiDAR. The JT128 user manual specification table lists a 95 degree vertical FOV from -4.4 degree to 90.5 degree, and notes that the vertical FOV values are vertical-angle projections onto a plane. For mechanical and perception coverage design, use the official JT128 manual, the 3D model, and real point cloud tests together rather than relying on one FOV number alone.
{% endhint %}

### Key Specifications

| Parameter                    | Hesai JT128                                                                                     | Engineering note                                                                                      |
| ---------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| Scanning method              | Mechanical rotation                                                                             | High-density spinning LiDAR; account for moving-platform motion distortion.                           |
| Channels                     | 128                                                                                             | Header channel number is fixed as 0x80 in the JT128 point cloud packet.                               |
| Instrumented range           | 0 to 60 m                                                                                       | Use reflectivity-specific ranging capability for application planning.                                |
| Ranging capability           | 40 m at 10 percent reflectivity, all channels                                                   | Important for dark objects and low-reflectivity obstacles.                                            |
| Ranging accuracy / precision | Typical +/-3 cm accuracy; 2 cm precision                                                        | May vary with range, temperature, and target reflectivity.                                            |
| Horizontal FOV               | 360 deg                                                                                         | Full horizontal surround coverage.                                                                    |
| Horizontal resolution        | 0.4 deg at 10 Hz; 0.8 deg at 20 Hz                                                              | Choose frame rate based on platform speed and point density needs.                                    |
| Vertical FOV                 | 95 deg projected vertical FOV, -4.4 deg to 90.5 deg                                             | See FOV note above regarding the marketed 360 x 189 deg hyper-hemispherical coverage.                 |
| Vertical resolution          | 0.74 deg average                                                                                | Dense vertical channel distribution for near-field 3D mapping.                                        |
| Frame rate                   | 10 / 20 Hz                                                                                      | Higher frame rate reduces horizontal resolution and increases power relative to typical conditions.   |
| Return mode                  | Single: First, Strongest, Last; Dual: Last & Strongest default, Last & First, First & Strongest | Dual return improves visibility in partially occluded or mixed-return scenes.                         |
| Wavelength / eye safety      | 905 nm, Class 1 eye safe                                                                        | Follow all laser safety and integration warnings in the manual.                                       |
| Ingress protection           | IP6K7                                                                                           | Useful for industrial and outdoor robots; still protect connectors and cabling.                       |
| Dimensions                   | Height 73.05 mm; bottom diameter 62.50 mm                                                       | Hesai also notes embedded installation with only 23.8 mm exposed window height on the product page.   |
| Weight                       | Less than 250 g                                                                                 | Official product page lists 250 g; manual lists less than 250 g.                                      |
| Voltage and power            | DC 9 to 32 V; 9.5 W typical                                                                     | Provide at least 2.6 A / 30 W input power; peak power can rise during cold starts or 20 Hz operation. |
| Operating temperature        | -20 deg C to 65 deg C                                                                           | Surface/internal temperatures may exceed ambient temperature.                                         |
| Storage temperature          | -40 deg C to 85 deg C                                                                           | Store and transport with shock protection.                                                            |
| Data interface               | Standard 100Base-TX Ethernet                                                                    | Use proper shielding, grounding, and packet-loss checks.                                              |
| Measurements                 | Distance, azimuth angle, reflectivity                                                           | JT128 packet data also includes confidence, sequence, and IMU fields in supported packet structure.   |
| Valid point rate             | Single return: 1,152,000 points/s; dual return: 2,304,000 points/s                              | Network and CPU pipelines must be sized for this throughput.                                          |
| Point cloud data rate        | Single return: 41.15 Mbps; dual return: 82.30 Mbps                                              | Use dedicated Ethernet where possible.                                                                |
| Clock source                 | GNSS / PTP 1588v2 / 802.1AS / 802.1AS Automotive                                                | Important for sensor fusion and multi-sensor robot stacks.                                            |

### Hardware Integration Notes

* Download the official JT128 3D model before cutting panels, brackets, robot skins, or embedded sensor windows.
* Remove the protective cover from the cover lens before operation.
* Keep the cover lens clean and avoid occluding the exposed optical window.
* Hesai strongly recommends chassis grounding for data integrity and ESD protection: mount the LiDAR on a grounded metal bracket and ensure electrical continuity through enclosure, screws, and bracket.
* If chassis grounding is impossible, use high-quality shielded twisted-pair Ethernet with properly grounded connectors.
* Design for at least 30 W input power headroom. The manual notes typical 9.5 W power, but recommends at least 2.6 A / 30 W external supply capability and states peak power remains below 30 W.
* Use appropriate screw torque; the manual notes the threaded-hole base material is aluminum alloy, so over-tightening can damage threads.
* Do not disassemble the product unless explicitly agreed in writing by Hesai.

### Network, Data, and Timing

| Topic                   | Default / detail                                                                                        | Integration guidance                                                                                  |
| ----------------------- | ------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| LiDAR IPv4 source       | 192.168.1.201                                                                                           | Set the host to 192.168.1.X, where X is 2-200 or 202-254.                                             |
| Subnet / gateway        | 255.255.255.0 / 192.168.1.1                                                                             | Keep host and LiDAR in the same subnet unless intentionally routing.                                  |
| Point cloud destination | 255.255.255.255 by default                                                                              | Broadcast works for bench testing; production networks may prefer explicit destination configuration. |
| UDP ports               | Source port 10000; destination point cloud port 2368; fault message port 2369                           | Open firewall rules and isolate high-rate LiDAR traffic from unrelated Ethernet devices.              |
| PTC port                | 9347                                                                                                    | Used for parameter setting, device status, firmware/software operations through Hesai tools/API.      |
| VLAN                    | VLAN ID 1 to 4094 when tagging is used                                                                  | Host and LiDAR VLAN IDs must match.                                                                   |
| Packet size             | Point Cloud Data Packet: 1146 bytes, including 1100 bytes UDP data                                      | Useful for packet capture, diagnostics, and custom decoders.                                          |
| Distance unit           | Dis Unit fixed at 4 mm                                                                                  | Object distance equals Distance field multiplied by Dis Unit.                                         |
| Return mode codes       | First 0x33, Strongest 0x37, Last 0x38, Last & Strongest 0x39, Last & First 0x3B, First & Strongest 0x3C | Confirm decoder and driver settings match the configured LiDAR mode.                                  |
| Clock sync              | GNSS or PTP 1588v2 / 802.1AS                                                                            | Validate timestamps before SLAM, multi-LiDAR, camera-LiDAR fusion, or robot navigation testing.       |

### Software Workflow

{% stepper %}
{% step %}
### Bench network setup

Set the host IP to the 192.168.1.x subnet, disable or configure firewall rules, and ping 192.168.1.201.
{% endstep %}

{% step %}
### Visualize first

Use PandarView 2 to confirm point cloud output, return mode, frame rate, packet reception, and time synchronization state.
{% endstep %}

{% step %}
### Save known-good configuration

Record IP, VLAN, port, frame rate, return mode, clock source, firmware/software versions, and angle correction file version.
{% endstep %}

{% step %}
### Integrate SDK or ROS

Use HesaiLidar SDK 2.0 for C++/PCAP/online parsing, or HesaiLidar ROS 2.0 for ROS1 and ROS2 point cloud publishing.
{% endstep %}

{% step %}
### Validate calibration

Load the correct JT128 angle correction file and confirm the point cloud looks geometrically consistent in PandarView or RViz.
{% endstep %}

{% step %}
### Run robot tests

Record indoor, outdoor, low-light, bright-light, dark-object, glass, reflective, dusty, rainy, and vibration-heavy cases.
{% endstep %}

{% step %}
### Monitor packet loss

High point rates need a clean Ethernet path, enough CPU, and driver settings matched to the selected return mode.
{% endstep %}
{% endstepper %}

### Official Downloads and Resources

| Resource                       | Use                                                                                      | Link                                                                                                                             |
| ------------------------------ | ---------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| OpenELAB product page          | Purchase and listing details                                                             | [OpenELAB Hesai JT128 page](https://openelab.io/products/hesai-jt128-3d-lidar-avg)                                               |
| Hesai JT128 product page       | Official product overview and key specifications                                         | [Hesai JT128 official page](https://www.hesaitech.com/product/jt128/)                                                            |
| Hesai downloads page           | Manuals, PandarView 2, 3D model, angle correction, and LidarUtilities                    | [Hesai downloads - JT128 section](https://www.hesaitech.com/downloads/#jt128)                                                    |
| JT128 User Manual              | Safety, installation, networking, data packet structure, specifications, troubleshooting | [JT128 User Manual PDF](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf)                |
| JT128 3D model                 | Mechanical design and embedded installation planning                                     | [JT128-3D-Model.zip](https://www.hesaitech.com/wp-content/uploads/2025/09/JT128-3D-Model.zip)                                    |
| JT128 default angle correction | Point cloud correction / calibration reference                                           | [JT128\_default\_angle.csv](https://www.hesaitech.com/wp-content/uploads/2026/05/JT128_default_angle.csv)                        |
| PandarView 2 Windows           | Point cloud visualization and recording                                                  | [PandarView Windows V2.1.7](https://www.hesaitech.com/wp-content/uploads/2025/01/PandarView_Release_Win64_V2.1.7.zip)            |
| PandarView 2 Ubuntu            | Linux visualization and bench testing                                                    | [PandarView Ubuntu V2.1.7](https://www.hesaitech.com/wp-content/uploads/2025/01/PandarView2_Release_Ubuntu_V2.1.7.zip)           |
| PandarView 2 User Manual       | Visualization software reference                                                         | [PandarView 2 User Manual PDF](https://www.hesaitech.com/wp-content/uploads/2025/08/PandarView2_User_Manual_PV2-en-250810.pdf)   |
| LidarUtilities JT128 Windows   | Device configuration/status/upgrade utility                                              | [Windows package](https://www.hesaitech.com/wp-content/uploads/2025/09/LidarUtilities_Sample_JT128_3.0.5_65677db_windows7.zip)   |
| LidarUtilities JT128 Ubuntu 20 | Linux utility package                                                                    | [Ubuntu 20 package](https://www.hesaitech.com/wp-content/uploads/2025/09/LidarUtilities_Sample_JT128_3.0.5_65677db_ubuntu20.zip) |
| LidarUtilities JT128 Ubuntu 22 | Linux utility package                                                                    | [Ubuntu 22 package](https://www.hesaitech.com/wp-content/uploads/2025/09/LidarUtilities_Sample_JT128_3.0.5_65677db_ubuntu22.zip) |
| HesaiLidar SDK 2.0             | C++ SDK, online parsing, PCAP parsing, visualization, PCD saving, packet-loss statistics | [HesaiTechnology/HesaiLidar\_SDK\_2.0](https://github.com/HesaiTechnology/HesaiLidar_SDK_2.0)                                    |
| HesaiLidar ROS 2.0             | ROS1/ROS2 driver based on SDK 2.0; publishes point clouds from UDP packets               | [HesaiTechnology/HesaiLidar\_ROS\_2.0](https://github.com/HesaiTechnology/HesaiLidar_ROS_2.0)                                    |

{% hint style="info" %}
Some direct Hesai file URLs may be protected by the website security layer in automated clients. If a direct file URL does not download in a script, open the official Hesai downloads page in a browser and use the JT128 section.
{% endhint %}

### Engineering Setup Checklist

* Download the JT128 user manual, 3D model, angle correction file, PandarView 2, LidarUtilities, SDK 2.0, and ROS 2.0 driver.
* Design the mechanical mount around the 62.50 mm bottom diameter, 73.05 mm height, connector routing, exposed optical window, grounding, and thermal constraints.
* Provide DC 9 to 32 V power with at least 30 W capacity at the LiDAR connector.
* Use dedicated or well-managed 100Base-TX Ethernet for the 41.15 to 82.30 Mbps point cloud stream.
* Set host IP to the correct 192.168.1.x address and verify UDP reception on 2368 and fault messages on 2369.
* Load or reference the correct JT128 angle correction file before evaluating geometry.
* Confirm return mode and frame rate in both device configuration and driver configuration.
* Verify timestamps with GNSS or PTP before multi-sensor fusion.
* Run packet-loss, vibration, thermal, and weather/environment tests before production deployment.

### Best Practices and Limitations

* **Do not treat JT128 as a complete safety system by itself.** It can support navigation and obstacle perception, but safety-rated functions require system-level safety analysis, redundancy, and certified hardware where required.
* **Account for network throughput.** Dual-return operation can reach 82.30 Mbps of point cloud data before ROS overhead, logging, or visualization load.
* **Validate near-field blind spots and robot body occlusions.** The compact hemispherical design is strong for embedded robotics, but every enclosure and bracket changes usable coverage.
* **Use the angle correction file.** Incorrect or missing correction data can make mapping, localization, and obstacle geometry appear wrong.
* **Test material edge cases.** Glass, dark rubber, polished metal, rain, fog, dust, and low-angle sunlight can affect point cloud quality.
* **Plan for serviceability.** Keep the lens accessible for cleaning and the network/power connectors accessible for diagnostics.

### Project References and Application Ideas

* [HesaiLidar SDK 2.0](https://github.com/HesaiTechnology/HesaiLidar_SDK_2.0): official SDK supporting JT128, online LiDAR parsing, PCAP parsing, point cloud visualization, PCD export, GPU acceleration, and packet-loss analysis.
* [HesaiLidar ROS 2.0](https://github.com/HesaiTechnology/HesaiLidar_ROS_2.0): official ROS/ROS2 driver supporting JT128; a practical starting point for RViz, mapping, navigation, and robot autonomy stacks.
* [Agtonomy autonomous farming reference](https://www.hesaitech.com/hesais-jt-series-3d-lidar-revolutionizes-the-future-of-autonomous-farming/): Hesai states that Agtonomy integrates JT128 LiDAR with autonomous farming robots for fleet monitoring and task automation.
* [Thoro.ai smart logistics reference](https://www.hesaitech.com/hesai-powers-safety-certified-ai-autonomy-for-smart-logistics-with-3d-lidar-at-modex-2026/): Hesai describes JT128 integration with Thoro.ai autonomy software for autonomous mobile robots.
* [Hesai JT Series launch reference](https://www.hesaitech.com/hesai-unveils-mini-hyper-hemispherical-3d-lidar-series-for-robotics-at-ces-hesai/): Hesai positions JT128 for robotics applications including autonomous agriculture and high-coverage robot perception.
* Application ideas: AGV/AMR navigation, pallet and rack perception, autonomous lawn and farm robots, robot docking, indoor/outdoor SLAM, smart logistics, 3D obstacle maps, and multi-sensor robot perception.

### FAQ

<details>

<summary>What is the Hesai JT128 used for?</summary>

The Hesai JT128 is used for 3D perception in AGVs, AMRs, robots, autonomous farming platforms, smart logistics robots, mapping systems, and navigation stacks that need compact 360 degree LiDAR coverage.

</details>

<details>

<summary>Does JT128 support ROS and ROS2?</summary>

Yes. HesaiLidar ROS 2.0 supports JT128 and provides ROS1/ROS2 point cloud publishing based on HesaiLidar SDK 2.0.

</details>

<details>

<summary>Which SDK should I use?</summary>

Use HesaiLidar SDK 2.0 for C++ integration, PCAP parsing, online LiDAR parsing, visualization, PCD export, and packet-loss analysis. Use HesaiLidar ROS 2.0 when integrating with ROS or ROS2.

</details>

<details>

<summary>What is the default JT128 IP address?</summary>

The JT128 manual lists the default LiDAR source IPv4 address as 192.168.1.201. Configure the host computer to the same subnet, avoiding 192.168.1.201 itself.

</details>

<details>

<summary>Which ports should be open?</summary>

The manual lists source UDP port 10000, destination point cloud UDP port 2368, fault message destination port 2369, and PTC port 9347.

</details>

<details>

<summary>Why does the FOV say both 360 x 189 degrees and 95 degrees vertical?</summary>

Hesai markets the JT128/64P series as 360 x 189 degree hyper-hemispherical. The user manual specification table lists 95 degrees projected vertical FOV and explains that vertical FOV values are projections onto a plane. Engineers should use the manual, 3D model, and real point cloud validation for final coverage design.

</details>

<details>

<summary>Can JT128 replace a safety LiDAR?</summary>

No by itself. JT128 can provide perception data for obstacle detection and navigation, but safety-rated stopping and protective functions require certified system-level safety design.

</details>

<details>

<summary>Where can I download the manual, CAD, correction file, and tools?</summary>

Use the official Hesai downloads page and the direct links in the resources table above. If a direct file URL is blocked by website security in automated clients, open the downloads page manually in a browser.

</details>

### Source Notes

* Product details: [OpenELAB Hesai JT128 product page](https://openelab.io/products/hesai-jt128-3d-lidar-avg).
* Official product and specifications: [Hesai JT128 product page](https://www.hesaitech.com/product/jt128/) and [JT128 User Manual](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf).
* Official downloads: [Hesai downloads page, JT128 section](https://www.hesaitech.com/downloads/#jt128).
* Official software: [HesaiLidar SDK 2.0](https://github.com/HesaiTechnology/HesaiLidar_SDK_2.0) and [HesaiLidar ROS 2.0](https://github.com/HesaiTechnology/HesaiLidar_ROS_2.0).
* Application references: Hesai JT Series agriculture and smart logistics newsroom references linked above.

**Review date:** 2026-05-25. Hesai documentation, correction files, SDKs, drivers, and product specifications can change; verify the latest official downloads and manuals before production deployment.
