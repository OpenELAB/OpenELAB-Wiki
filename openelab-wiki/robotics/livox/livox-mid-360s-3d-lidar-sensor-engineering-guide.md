# Livox MID-360S 3D LiDAR Sensor Engineering Guide

{% hint style="info" %}
[**View Livox MID-360S (sensor-only) on OpenELAB**](https://openelab.io/products/livox-mid360) · [**View Livox MID-360S Kit on OpenELAB**](https://openelab.io/products/livox-mid360)

**Model:** Livox MID-360S · **SKUs:** `Livox-MID-360S` (sensor only), `Livox-MID-360S-Kit` (includes 1.5 m splitter cable and power adapter) · **Selection:** choose the corresponding option on the product page.
{% endhint %}

[Product link: Livox MID-360S 3D LiDAR Sensor on OpenELAB](https://openelab.io/products/livox-mid360?variant=45625733185734)

The Livox MID-360S is a compact 360 degree 3D LiDAR for mobile robots, SLAM, localization, obstacle avoidance, and mapping. It provides 59 degree vertical FOV, 0.1 m minimum range, 200,000 points/s, 10 Hz typical frame rate, 100BASE-TX Ethernet, IEEE 1588-2008 PTP v2/GPS sync, built-in ICM40609 IMU, 9-27 V DC input, and IP67 protection. The provided OpenELAB link selects the MID-360S variant; the same listing offers the MID-360S sensor-only and MID-360S-Kit purchase options. The original MID-360 is a separate model and uses different firmware downloads.

## Quick Summary

* **Covered variants:** MID-360S sensor-only (`Livox-MID-360S`) and MID-360S-Kit (`Livox-MID-360S-Kit`, with 1.5 m splitter cable and power adapter). Both use the same MID-360S LiDAR; the kit changes the included connection accessories.
* **Use cases:** AMR navigation, service robots, autonomous forklifts, outdoor robots, 3D mapping, obstacle avoidance, and LiDAR-inertial odometry.
* **Software:** Livox Viewer 2, Livox SDK2, Livox ROS Driver 2, ROS/ROS2 SLAM packages such as FAST-LIO, MOLA, and LIO-SAM adaptations.
* **Category:** sensors / LiDAR / 3D perception.

## MID-360S vs MID-360

| Parameter               | MID-360                                                          | MID-360S                                                   |
| ----------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------- |
| FOV                     | 360 deg horizontal; -7 deg to 52 deg vertical                    | 360 deg horizontal; 59 deg vertical                        |
| Range                   | 40 m at 10 percent reflectivity; 70 m at 80 percent reflectivity | 40 m at 10 percent reflectivity; up to 100 m cut-off range |
| Minimum range           | 0.1 m                                                            | 0.1 m                                                      |
| Point rate / frame rate | 200,000 points/s; 10 Hz typical                                  | 200,000 points/s; 10 Hz typical                            |
| Interface               | 100BASE-TX Ethernet; PTP v2/GPS sync                             | 100BASE-TX Ethernet; PTP v2/GPS sync                       |
| IMU                     | ICM40609                                                         | ICM40609                                                   |
| Power                   | 6.5 W typical, 9-27 V DC                                         | 6.5 W typical, 9-27 V DC                                   |
| Size / weight           | 65 x 65 x 60 mm; approx. 265 g                                   | 65 x 65 x 60 mm; approx. 265 g                             |
| Protection              | IP67                                                             | IP67                                                       |

**Accuracy note:** Livox's official MID-360S product page lists 265 g. Treat the 905 g text in some reseller copy as likely incorrect unless confirmed by Livox.

## Hardware Integration

* Use the official STP 3D model and FOV model before designing brackets, covers, or robot bodywork.
* Keep the optical window and vertical FOV clear of payloads, handles, antennas, cables, and protective cages.
* OpenELAB notes the MID-360S M12 aviation connector is retracted inward by 2 mm and shifted upward by 3 mm versus MID-360; verify cable clearance when reusing enclosures.
* Provide clean regulated 9-27 V DC power and avoid motor-noise coupling.
* Use PTP v2 or GPS synchronization for multi-sensor fusion, especially LiDAR+IMU+camera stacks.

## Getting started: first point-cloud capture

### Prerequisites

* MID-360S sensor, the official 1-to-3 splitter cable and a manufacturer-compatible **9–27 V DC** power supply. The kit includes the splitter cable and power adapter; obtain those separately for the sensor-only option. Use the official user manual to confirm connector alignment, polarity and the power supply.
* A computer with a wired Ethernet port and a supported Livox Viewer 2 build. [Get Viewer 2 and the MID-360S manual from Livox](https://www.livoxtech.com/mid-360s/downloads).
* A clear observation area, with no other LiDAR beams directly opposing the sensor.

### Connection and first result

1. **Configure the host network before connecting.** On the Ethernet adapter used for the sensor, set the IPv4 address to `192.168.1.50` and subnet mask to `255.255.255.0`. Livox documents the factory LiDAR address as `192.168.1.1XX`, where `XX` is the last two digits of its serial number. Confirm there is no address conflict.
2. **Connect with power off.** Align the M12 aviation connector and its positioning key without forcing the pins. Attach the splitter cable's Ethernet RJ-45 plug to the computer and the power lead to the compatible supply according to the _MID-360S User Manual_, §§ 1.2 and 3.3. The Ethernet port is a data connection, **not a PoE power input**.
3. **Power on and launch Livox Viewer 2.** On Windows, launch the application from the extracted download; on supported Ubuntu builds run `./livox_viewer_2.sh` from its extracted directory. Select the discovered MID-360S, confirm its serial number and firmware version, and switch it to the **Sampling** mode using the Viewer controls.
4. **Verify one live capture.** Inspect the real-time 3D point cloud and change the view or present a stationary target. Record the observed sensor address, serial number, firmware and Viewer version before moving to an SDK or ROS integration.

**Expected result:** the device is discoverable in Livox Viewer 2, reports a normal working state and displays live point-cloud samples. This procedure is a documented **first-result workflow**, not a hardware test performed by OpenELAB.

**If discovery or capture fails:** check the adapter address and subnet first, then the connector and 9–27 V power, competing software connections, Ethernet broadcasts/firewall rules and device operating state. The manufacturer's troubleshooting section also recommends packet inspection (for example Wireshark) when no data arrives.

_Source:_ [_Livox MID-360S User Manual, v1.0 (2026), §§ 3.3 and 3.6–3.7, 5.1_](https://www.livoxtech.com/mid-360s/downloads)_._

## Software Workflow

{% stepper %}
{% step %}
## Bench test the sensor

Use Livox Viewer 2 and confirm firmware, point cloud, IMU, and network settings.
{% endstep %}

{% step %}
## Install the software

Install Livox SDK2 for C/C++ applications or Livox ROS Driver 2 for ROS/ROS2.
{% endstep %}

{% step %}
## Verify the data flow

Choose the message format and verify point cloud frequency, IMU frequency, timestamps, frame IDs, and TF tree.
{% endstep %}

{% step %}
## Measure the extrinsics

Measure the LiDAR-to-base transform carefully; SLAM quality is sensitive to extrinsic calibration.
{% endstep %}

{% step %}
## Run mapping or localization

Run mapping/localization with FAST-LIO, MOLA, LIO-SAM adaptations, or your preferred navigation stack, then tune for speed, vibration, and environment geometry.
{% endstep %}
{% endstepper %}

## Official Downloads and Resources

| Resource                    | Use                                                    | Link                                                                                                                                                                                                                                                                                 |
| --------------------------- | ------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| OpenELAB product page       | Purchase and variant selection                         | [OpenELAB MID-360S page](https://openelab.io/products/livox-mid360?variant=45625733185734)                                                                                                                                                                                           |
| Livox MID-360S product page | Official specs and overview                            | [Livox MID-360S](https://www.livoxtech.com/mid-360s)                                                                                                                                                                                                                                 |
| Livox MID-360S downloads    | Official manuals, CAD, Viewer, firmware, release notes | [MID-360S downloads](https://www.livoxtech.com/mid-360s/downloads)                                                                                                                                                                                                                   |
| User manual                 | Installation, cabling, configuration, safety           | [User Manual PDF](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360S/UM/Livox_Mid-360s_User_Manual_en.pdf)                                                                                                                                                       |
| Product information         | Compliance and product notes                           | [Product Information PDF](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360S/PI/Livox_Mid-360s_Product_Information.pdf)                                                                                                                                          |
| CAD model                   | Mechanical integration                                 | [MID-360S STP model](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360S/Mid-360S%203D%20Model/mid-360S.stp)                                                                                                                                                      |
| FOV model                   | Blind-zone and occlusion checking                      | [MID-360S FOV STP model](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360S/Mid-360S%20FOV%E6%95%B0%E6%A8%A1/mid-360s_fov.stp)                                                                                                                                   |
| Splitter cable model        | Cable routing design                                   | [Splitter cable STP](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Livox%20%E8%88%AA%E6%8F%92%E4%B8%80%E5%88%86%E4%B8%89%E7%BA%BF.stp)                                                                                                                      |
| Livox Viewer 2              | Visualization and bench testing                        | [Windows](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360S/Livox%20Viewer%202%20-%20Windows/Viewer2_2.5.9_Windows.zip) / [Ubuntu](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360S/Livox%20Viewer%202-%20Ubuntu/Viewer2_2.5.9_Linux.zip) |
| Release notes and firmware  | Update planning                                        | [Current MID-360S release notes and firmware](https://www.livoxtech.com/mid-360s/downloads) (Livox listed 35.01.0113 on 2026-10-30; verify exact model/revision before any update)                                                                                                   |
| SDK and ROS driver          | Development                                            | [Livox SDK2](https://github.com/Livox-SDK/Livox-SDK2) / [Livox ROS Driver 2](https://github.com/Livox-SDK/livox_ros_driver2)                                                                                                                                                         |

## MID-360 Original Variant Resources

If you buy the original MID-360 variant, use the [Livox MID-360 downloads page](https://www.livoxtech.com/mid-360/downloads) for its firmware, quick-start guide, sample data, Viewer packages, and CAD. Do not flash MID-360S firmware onto MID-360 hardware unless Livox explicitly confirms compatibility.

## Engineering Setup Checklist

* Confirm variant: MID-360S or MID-360.
* Download the correct manual, release notes, firmware, CAD model, and FOV model.
* Design the mount and verify FOV clearance in CAD.
* Bench test with Livox Viewer 2 before installing on the robot.
* Install Livox SDK2 or Livox ROS Driver 2.
* Configure static IP/network routing and publish accurate TF/extrinsic transforms.
* Validate timestamps before running SLAM.
* Record firmware, driver version, ROS distribution, and SLAM package versions.

## Best Practices and Limitations

* Mount high enough to avoid chassis occlusion while preserving near-field obstacle detection.
* Protect the optical window from dust, water spots, fingerprints, and impact.
* Use stable power and robust Ethernet strain relief on mobile platforms.
* Validate dark, glossy, glass, thin, and low-reflectivity obstacles in the real operating environment.
* Do not rely on SLAM alone for functional safety; safety-rated robot functions require system-level safety design.

## Project References and Application Ideas

* [Livox ROS Driver 2](https://github.com/Livox-SDK/livox_ros_driver2): official ROS/ROS2 integration starting point.
* [MOLA MID-360 example](https://github.com/Whan000/MOLA-SLAM): ROS2 Humble MID-360 mapping/localization example.
* [fast\_lio\_tinker](https://github.com/tinkerfuroc/fast_lio_tinker): FAST-LIO2-oriented MID-360 mobile robot workflow.
* [LIO-SAM-MID360](https://github.com/nkymzsy/LIO-SAM-MID360): LIO-SAM adaptation for Livox MID360-style data.
* [CMU mecanum autonomy stack](https://github.com/jizhang-cmu/autonomy_stack_mecanum_wheel_platform): ROS2 autonomy platform referencing Livox Mid-360 integration.
* Application ideas: AMR navigation, forklift perception, warehouse mapping, service robot localization, outdoor robot obstacle detection, and research-grade LiDAR-inertial odometry.

## FAQ

<details>

<summary>What is the Livox MID-360S used for?</summary>

It is used for 3D perception on mobile robots, including SLAM, localization, obstacle avoidance, navigation, mapping, and autonomous system research.

</details>

<details>

<summary>Does MID-360S work with ROS2?</summary>

Yes. Livox provides Livox ROS Driver 2 for ROS and ROS2 integration.

</details>

<details>

<summary>Which SDK should I use?</summary>

Use Livox SDK2 for C/C++ integration and Livox ROS Driver 2 for ROS/ROS2 robotics workflows.

</details>

<details>

<summary>Where can I download CAD and FOV models?</summary>

Use the official MID-360S downloads page or the direct STP links in the resource table above.

</details>

<details>

<summary>Can it replace a safety LiDAR?</summary>

No by itself. It can support perception and obstacle avoidance, but safety-rated functions require dedicated safety design and compliance validation.

</details>

## Source Notes

* Product and variant details: [OpenELAB Livox MID-360S product page](https://openelab.io/products/livox-mid360?variant=45625733185734)
* Official specifications and downloads: [Livox MID-360S product page](https://www.livoxtech.com/mid-360s), [MID-360S downloads](https://www.livoxtech.com/mid-360s/downloads)
* SDK and ROS/ROS2: [Livox SDK2](https://github.com/Livox-SDK/Livox-SDK2), [Livox ROS Driver 2](https://github.com/Livox-SDK/livox_ros_driver2)
* Project references: [MOLA MID-360 example](https://github.com/Whan000/MOLA-SLAM), [fast\_lio\_tinker](https://github.com/tinkerfuroc/fast_lio_tinker), [LIO-SAM-MID360](https://github.com/nkymzsy/LIO-SAM-MID360)

**Original guide review:** 2026-05-25. **Targeted update:** 2026-11-18 (store SKU/kit scope, first-use network procedure and Livox firmware listing). Remaining specifications and third-party project links have not been independently revalidated in this update. **Software execution:** not run. **Hardware validation:** not run. Check current Livox release notes before production deployment.

### <sub>Download Center</sub>

{% file src="../../.gitbook/assets/Livox MID-360S KCC Certification Certificate.pdf" %}

{% file src="../../.gitbook/assets/Livox MID-360S ROHS Certification Certificate.pdf" %}

{% file src="../../.gitbook/assets/Livox MID-360S SVHC Certification Certificate.pdf" %}

{% file src="../../.gitbook/assets/Livox MID-360S_CB Certification Certificate.pdf" %}

{% file src="../../.gitbook/assets/Livox MID-360S_CE Certification Certificate.pdf" %}

{% file src="../../.gitbook/assets/Livox MID-360S_FCC Certification Certificate.pdf" %}
