# Unitree L2 4D LiDAR Engineering Guide

{% hint style="info" %}
[**View Unitree L2 4D LiDAR on OpenELAB**](https://openelab.io/products/unitree-l2-4dlidar-navigation-obstacle-avoidance-slam-360-depth-scan)

**Product/option:** Unitree L2 4D LiDAR · **Workbook SKU:** `Unitree-L24DLiDAR`
{% endhint %}

**Product link:** [Unitree L2 4D LiDAR Navigation Obstacle Avoidance SLAM 360 Depth Scan on OpenELAB](https://openelab.io/products/unitree-l2-4dlidar-navigation-obstacle-avoidance-slam-360-depth-scan)

## Unitree L2 4D LiDAR Engineering Guide

The Unitree L2 is a compact 4D LiDAR sensor for mobile robots, SLAM, localization, obstacle avoidance, 3D reconstruction, and environmental scanning. It outputs 3D position plus 1D grayscale point cloud data, includes a built-in 3-axis accelerometer and 3-axis gyroscope, supports ENET UDP and TTL UART, and is designed for low-speed robotics platforms that need wide field-of-view perception in a small 230 g package.

### Quick Summary

* **Product:** Unitree 4D LiDAR-L2, OpenELAB SKU Unitree-L24DLiDAR.
* **Best fit:** AMRs, quadrupeds, service robots, smart cleaning robots, indoor mapping, warehouse navigation, and research SLAM platforms.
* **Core perception:** 360 deg x 90 deg standard FOV, or 360 deg x 96 deg negative-angle mode.
* **SLAM workflow:** Unitree provides Unilidar SDK2, ROS/ROS2 packages, and a Point-LIO adaptation for Unitree L1/L2 LiDAR.
* **Important purchase note:** The OpenELAB listing states this is the China version and comes with an EU plug adapter.

### Key Specifications

| Parameter             | Unitree L2                                                                 | Engineering note                                                                           |
| --------------------- | -------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| LiDAR data            | 3D position + 1D grayscale; supports 2D mode                               | Useful for geometry plus reflectivity-aware perception pipelines.                          |
| Field of view         | 360 deg x 90 deg; 360 deg x 96 deg in NEGA mode                            | The extra 6 deg in negative-angle mode has a shorter maximum measurement distance.         |
| Range                 | 30 m at 90 percent reflectivity; 15 m at 10 percent reflectivity           | Actual range depends on target reflectivity and environment.                               |
| Near blind zone       | 0.05 m                                                                     | Very useful for close obstacle perception, but near-range accuracy still needs validation. |
| Sampling frequency    | 128,000 points/s                                                           | Raw sampling rate.                                                                         |
| Effective frequency   | 64,000 points/s                                                            | Used for mapping and navigation point cloud output.                                        |
| Scanning method       | Contactless brushless mirror scanning                                      | Non-repetitive scanning pattern for dense spatial coverage.                                |
| Scanning frequency    | 5.55 Hz horizontal/circumferential; 216 Hz vertical                        | Consider motion distortion on fast platforms.                                              |
| Measurement accuracy  | Less than or equal to 2.0 cm                                               | Validate against real target materials and robot vibration.                                |
| Distance resolution   | 4.5 mm                                                                     | Official L2 parameter.                                                                     |
| IMU                   | 3-axis accelerometer + 3-axis gyroscope                                    | 1 kHz sampling, 500 Hz reporting frequency.                                                |
| Interfaces            | ENET UDP, TTL UART                                                         | Only one data output mode is selected at a time through Unilidar 2 or SDK.                 |
| TTL UART baud rate    | 4,000,000 bps                                                              | Use short, reliable wiring for embedded serial integration.                                |
| Default network       | L2 IP 192.168.1.62; target server 192.168.1.2; UDP send 6101; receive 6201 | Set the host IP carefully to avoid conflicts.                                              |
| Eye safety            | Class 1, IEC60825-1:2014                                                   | 905 nm pulsed laser per official manual.                                                   |
| Anti-glare ability    | 100 Klux                                                                   | Official page describes outdoor strong-light ranging stability.                            |
| Power                 | 12 V DC, 10 W typical at 25 deg C                                          | Power supply requirement is 12 V, 1 A; peak power can reach 13 W during self-heating.      |
| Operating temperature | -10 deg C to 50 deg C                                                      | At -10 deg C to 30 deg C, self-heating may delay point cloud output.                       |
| Storage temperature   | -20 deg C to 60 deg C                                                      | Store dry, ventilated, and dust-free.                                                      |
| Ingress protection    | IP54                                                                       | Add external water/dust protection for exposed robot deployments.                          |
| Size and weight       | 75 x 75 x 65 mm; 230 g                                                     | Four bottom M3 mounting holes, 6 mm depth.                                                 |

### Hardware Integration Notes

* Use the official STEP model before designing brackets, top covers, protective cages, or robot body panels.
* Keep the full FOV clear. Unitree specifically notes that even transparent glass over the optical window can affect performance.
* Do not use the L2 body as a load-bearing structure. The mounting structure should hold the sensor without adding external loads to it.
* Leave airflow around all sides for heat dissipation; long high-temperature operation can reduce performance or trigger over-temperature protection.
* Clean the optical window with a clean cloth or alcohol when needed. Dust, mud, fingerprints, or water marks can degrade point cloud quality.
* For water-sensitive installations, add external protection appropriate to the mounting angle. The official manual states protection varies with installation angle.

### Interface and Network Details

| Interface            | Details                                                          | Use case                                                                          |
| -------------------- | ---------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| Power                | DC3.5-1.35 power connector; 12 V DC input                        | Use the included adapter for bench testing, then design a clean robot power rail. |
| Ethernet             | RJ45 receptacle, ENET UDP output                                 | Recommended for ROS/ROS2 PCs, embedded Linux computers, and SLAM workstations.    |
| TTL UART             | GH1.25 4-pin serial plug, 4,000,000 bps                          | Useful for embedded systems or adapter-module testing.                            |
| Default IP           | L2: 192.168.1.62; gateway: 192.168.1.1; subnet: 255.255.255.0    | Set host to the same subnet, commonly 192.168.1.2 if using factory defaults.      |
| Default UDP ports    | LiDAR send port 6101; destination server receive port 6201       | Open firewall rules and confirm the port is not occupied.                         |
| Point cloud contents | Distance, angle, reflectivity, IMU data, and working-status data | Use timestamps, frame definitions, and IMU settings consistently in SLAM.         |

### Software Workflow

1. **Bench test first:** connect power and either Ethernet or TTL UART, then verify live point cloud display in Unilidar 2.
2. **Confirm output mode:** select ENET UDP or TTL UART; the L2 can output through only one of these modes at a time.
3. **Install SDK:** use Unitree Unilidar SDK2 for C++ applications or the included ROS/ROS2 packages for robotics middleware.
4. **Configure robot frames:** align the LiDAR coordinate system, IMU frame, robot base frame, and TF tree.
5. **Run SLAM:** start with Unitree point\_lio\_unilidar for ROS1/Noetic, or evaluate community ROS2 ports if the project is ROS2-first.
6. **Validate in motion:** record bags during turns, vibration, ramps, reflective surfaces, glass, dark objects, narrow obstacles, and outdoor sunlight.
7. **Document versions:** record firmware/software, SDK version, ROS distribution, IP settings, output mode, and SLAM parameters.

### Official Downloads and Resources

| Resource                    | Use                                                                                                | Link                                                                                                                                   |
| --------------------------- | -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| OpenELAB product page       | Purchase and listing details                                                                       | [OpenELAB Unitree L2 4D LiDAR page](https://openelab.io/products/unitree-l2-4dlidar-navigation-obstacle-avoidance-slam-360-depth-scan) |
| Unitree L2 product page     | Official product overview and specifications                                                       | [Unitree L2 official page](https://www.unitree.com/L2/)                                                                                |
| Unitree L2 download page    | Manuals, CAD, SDK, software, sample data                                                           | [Unitree L2 downloads](https://www.unitree.com/mobile/download/L2/)                                                                    |
| L2 User Manual              | Installation, interface definition, network defaults, maintenance, troubleshooting, specifications | [Unitree 4D LiDAR L2 User Manual PDF](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf)         |
| L2 3D model                 | Mechanical design and collision/FOV checking                                                       | [L2 3D Model STEP](https://oss-global-cdn.unitree.com/static/L2%203D%20Model.STEP)                                                     |
| Unilidar 2                  | Windows point cloud visualization and configuration                                                | [Unilidar 2 V1.21 Windows](https://oss-global-cdn.unitree.com/static/Unilidar_2_V1.21.exe)                                             |
| Unilidar 2 User Manual      | GUI operation and configuration reference                                                          | [Unilidar 2 User Manual PDF](https://oss-global-cdn.unitree.com/static/Unilidar%202%20User%20Manual.pdf)                               |
| Unilidar SDK2 archive       | Official SDK package from Unitree download page                                                    | [unilidar\_sdk2-2.0.4.zip](https://oss-global-cdn.unitree.com/static/unilidar_sdk2-2.0.4.zip)                                          |
| Unilidar SDK2 GitHub        | C++ SDK, ROS package, and ROS2 package for Unitree L2                                              | [unitreerobotics/unilidar\_sdk2](https://github.com/unitreerobotics/unilidar_sdk2)                                                     |
| Point-LIO for Unitree LiDAR | Official Unitree L1/L2 LiDAR-inertial odometry and mapping package                                 | [unitreerobotics/point\_lio\_unilidar](https://github.com/unitreerobotics/point_lio_unilidar)                                          |
| Point-LIO package archive   | Official download-page ZIP package                                                                 | [point\_lio\_unilidar-2.0.2.zip](https://oss-global-cdn.unitree.com/static/point_lio_unilidar-2.0.2.zip)                               |
| Indoor sample bag           | Test mapping pipeline without hardware                                                             | [L2 Indoor Point Cloud Data.bag](https://oss-global-cdn.unitree.com/static/L2%20Indoor%20Point%20Cloud%20Data.bag)                     |
| Park sample bag             | Outdoor test data for SLAM experiments                                                             | [L2 Park Point Cloud Data.bag](https://oss-global-cdn.unitree.com/static/L2%20Park%20Point%20Cloud%20Data.bag)                         |

### Engineering Setup Checklist

* Confirm the package contents: L2 LiDAR, adapter module, data cable, power adapter, rubber pad, screws, wrench, and EU plug adapter from OpenELAB listing.
* Download the L2 user manual, STEP model, Unilidar 2, SDK2, and Point-LIO package before mechanical integration.
* Design the mount around the 75 x 75 x 65 mm body, bottom M3 holes, cable exit, airflow, and full FOV clearance.
* Use 12 V DC power with enough margin for 10 W typical operation and up to 13 W peak self-heating behavior.
* For Ethernet, set the host network to the L2 subnet and verify UDP traffic on ports 6101 and 6201.
* Decide whether the robot will use 3D mode, 2D mode, standard FOV, negative-angle mode, grayscale output, and IMU output.
* Record the LiDAR-to-base transform and verify the point cloud frame against the SDK coordinate definition.
* Run Unilidar 2 on a stable bench setup before robot installation.
* Record representative indoor and outdoor bags for regression testing after any mount, power, firmware, or algorithm change.

### Best Practices and Limitations

* **Do not treat 4D LiDAR as a safety-rated scanner.** It can support navigation and obstacle avoidance, but safety functions require system-level safety design and compliance validation.
* **Watch motion distortion.** The L2 is well suited to low-speed mobile robots; fast rotations, aggressive vibration, and high-speed vehicles need extra validation.
* **Validate material edge cases.** Test glass, glossy black objects, thin table legs, reflective metal, dark fabric, strong sunlight, fog, dust, and low obstacles.
* **Keep the window clean.** Optical contamination directly affects point cloud quality.
* **Plan for heat.** Add airflow and avoid enclosing the sensor in a sealed hot compartment.
* **Synchronize correctly.** LiDAR-inertial odometry quality depends on accurate timing, IMU settings, and extrinsic calibration.

### Project References and Application Ideas

* [Unitree Unilidar SDK2](https://github.com/unitreerobotics/unilidar_sdk2): official SDK with C++ interfaces plus ROS and ROS2 packages for parsing and publishing Unitree L2 point cloud and IMU data.
* [Unitree point\_lio\_unilidar](https://github.com/unitreerobotics/point_lio_unilidar): official adaptation of Point-LIO for Unitree L1 and L2, with L2 video demos and sample data workflow.
* [point\_lio\_ros2 with Unitree L1/L2 support](https://github.com/dfloreaa/point_lio_ros2): community ROS2 port for engineers building ROS2-first LiDAR-inertial odometry stacks.
* [unilidar\_fastlio\_ros2](https://github.com/newkillerwhale/unilidar_fastlio_ros2): community ROS2 FAST-LIO-style integration for Unitree LiDAR.
* [Unitree Go2 L2 mapping reference](https://www.unitree.com/go2/): Unitree describes the Go2 robot using its L2 LiDAR for 360 deg x 96 deg recognition and 3D LiDAR mapping, showing a practical robot navigation application.
* Application ideas: indoor AMR localization, warehouse obstacle perception, quadruped mapping, service robot navigation, autonomous cleaning robot perception, educational SLAM labs, and low-speed outdoor survey robots.

### FAQ

<details>

<summary>What is the Unitree L2 4D LiDAR used for?</summary>

The Unitree L2 is used for mobile robot mapping, localization, obstacle avoidance, 3D scanning, recognition, and LiDAR-inertial SLAM. It is especially attractive for low-speed robots that need wide FOV perception in a compact sensor.

</details>

<details>

<summary>Does Unitree L2 support ROS and ROS2?</summary>

Yes. Unitree Unilidar SDK2 includes ROS and ROS2 packages, and Unitree provides a Point-LIO adaptation for L1/L2 LiDAR. Community ROS2 ports also exist, but engineers should review and test them before production use.

</details>

<details>

<summary>What is 4D LiDAR in the Unitree L2?</summary>

In Unitree's L2 documentation, 4D data means 3D position plus 1D grayscale or reflectivity-like information. It does not mean the sensor directly outputs semantic classification or velocity for every object.

</details>

<details>

<summary>Can the L2 operate outdoors?</summary>

Yes. Unitree specifies indoor/outdoor operation and 100 Klux anti-strong-light ability. Outdoor performance still depends on target reflectivity, weather, vibration, sunlight angle, and mounting protection.

</details>

<details>

<summary>Which interface should I use, Ethernet UDP or TTL UART?</summary>

Use Ethernet UDP for most robotics computers, ROS/ROS2 systems, and SLAM workloads. TTL UART can be useful for embedded integrations, but requires reliable wiring and a 4,000,000 bps serial path.

</details>

<details>

<summary>What are the default IP settings?</summary>

The official manual lists the L2 default IP as 192.168.1.62, gateway 192.168.1.1, subnet mask 255.255.255.0, default destination server IP 192.168.1.2, LiDAR UDP send port 6101, and destination receive port 6201.

</details>

<details>

<summary>Can the Unitree L2 replace a safety LiDAR?</summary>

No. The L2 can support perception and obstacle avoidance, but safety-rated stopping or protective functions require dedicated safety-rated hardware, risk assessment, and compliance validation.

</details>

<details>

<summary>Where can I download CAD, SDK, manuals, and sample data?</summary>

Use the official Unitree L2 download page and the direct links in the resource table above for the STEP model, user manual, Unilidar 2, SDK2, Point-LIO package, and sample rosbag files.

</details>

### Source Notes

* Product details and package note: [OpenELAB Unitree L2 4D LiDAR product page](https://openelab.io/products/unitree-l2-4dlidar-navigation-obstacle-avoidance-slam-360-depth-scan).
* Official specifications: [Unitree L2 product page](https://www.unitree.com/L2/) and [Unitree 4D LiDAR-L2 User Manual](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf).
* Official downloads: [Unitree L2 downloads](https://www.unitree.com/mobile/download/L2/).
* Official software: [Unilidar SDK2](https://github.com/unitreerobotics/unilidar_sdk2) and [point\_lio\_unilidar](https://github.com/unitreerobotics/point_lio_unilidar).
* Engineering references: [point\_lio\_ros2](https://github.com/dfloreaa/point_lio_ros2), [unilidar\_fastlio\_ros2](https://github.com/newkillerwhale/unilidar_fastlio_ros2), and [Unitree Go2 L2 mapping reference](https://www.unitree.com/go2/).

**Review date:** 2026-05-25. Unitree software, manuals, SDKs, sample data, and product specifications can change; verify official release notes and manuals before production deployment.
