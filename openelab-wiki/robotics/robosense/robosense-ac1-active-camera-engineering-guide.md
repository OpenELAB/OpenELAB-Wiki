# RoboSense AC1 Active Camera Engineering Guide

{% hint style="info" %}
[**View RoboSense AC1 Active Camera on OpenELAB**](https://openelab.io/products/robosense-ac1-lidar-depth-camera-pre-sale)

**Product model/family:** RoboSense AC1 Active Camera · **OpenELAB SKU:** `RS-AC1`
{% endhint %}

Product link: https://openelab.io/products/robosense-ac1-lidar-depth-camera-pre-sale

![RoboSense AC1 product image](<../../.gitbook/assets/robosense ac1 product.jpg>)

RoboSense AC1 is an active camera sensor that combines a Time-of-Flight LiDAR depth sensor, RGB camera, and 6-axis IMU for robot perception. This OpenELAB wiki guide is based on the AC1 user manual and OpenELAB product listing. It focuses on practical engineering integration: USB 3.2 Gen1 data connection, DC power, AC Viewer setup, point cloud/image/IMU output, and revision checks. The source PDF contains an early-page `E1R User Guide` label while the main content and product listing identify the product as AC1, so confirm the final hardware and manual revision before production use.

## Overview

AC1 is intended for intelligent robot vision, autonomous navigation, 3D depth sensing, and machine perception workflows where a compact sensor must provide depth, RGB image, and IMU data to a host computer. Unlike Ethernet LiDAR products such as RoboSense Fairy or EM4, AC1 uses USB output and AC Viewer rather than RSView for first bring-up.

## Product And Variant Information

| Item                 | Value                                                                   |
| -------------------- | ----------------------------------------------------------------------- |
| Product name         | RoboSense Active Camera AC1 LiDAR Depth Camera Intelligent Robot Vision |
| Brand / manufacturer | RoboSense / Suteng Innovation Technology Co., Ltd.                      |
| OpenELAB vendor      | RoboSense                                                               |
| OpenELAB handle      | `robosense-ac1-lidar-depth-camera-pre-sale`                             |
| Variant              | Default Title                                                           |
| SKU                  | `JD-RS-AC1`                                                             |
| Manual version       | 1.0                                                                     |
| Manual revision date | 2025-04-11                                                              |

## Specifications

| Category                | Specification                                         |
| ----------------------- | ----------------------------------------------------- |
| LiDAR ranging principle | Time of Flight                                        |
| LiDAR wavelength        | 940 nm                                                |
| Laser safety            | Class 1 eye safe                                      |
| LiDAR FOV               | 120 deg horizontal, 60 deg vertical                   |
| LiDAR range             | 20 m at 10 percent NIST target, environment dependent |
| Blind area              | 0.1 m at 90 percent target                            |
| Ranging precision       | +/-3 cm at 1 sigma indoor, +/-5 cm at 1 sigma outdoor |
| Point rate              | About 173,333 points/s                                |
| LiDAR frame rate        | 10 Hz                                                 |
| RGB shutter             | Rolling shutter                                       |
| RGB FOV                 | 144 deg horizontal, 78 deg vertical                   |
| RGB output format       | NV12, RGB24                                           |
| RGB frame rate          | 30 Hz                                                 |
| RGB resolution          | 1920 x 800                                            |
| IMU                     | 6-axis output                                         |
| Gyroscope               | +/-2000 dps                                           |
| Accelerometer           | +/-16 g                                               |
| IMU data frequency      | 200 Hz adjustable                                     |
| Typical power           | 12.6 W                                                |
| Operating temperature   | -20 C to +60 C                                        |
| Storage temperature     | -20 C to +70 C                                        |
| Protection rating       | IP54                                                  |
| Weight                  | 400 g +/-10 percent                                   |
| Data interface          | USB 3.2 Gen1                                          |
| Power interface         | DC                                                    |
| Size                    | 95 mm x 42.6 mm x 80 mm                               |

## Hardware Architecture

| Module                 | Function                                                             |
| ---------------------- | -------------------------------------------------------------------- |
| LiDAR depth module     | Produces depth/point-cloud data using Time-of-Flight ranging         |
| RGB camera             | Provides 1920 x 800 image output in NV12 or RGB24 format             |
| IMU                    | Provides 6-axis motion data for perception and calibration workflows |
| USB 3.2 Gen1 interface | Carries LiDAR, image, and IMU data to the host computer              |
| DC power input         | Supplies power through the screw-lock DC power cable                 |

## Wiring And Interface

| Interface            | Manual note                                                                                                            |
| -------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| Data                 | USB 3.2 Gen1, Type-C cable with screw lock                                                                             |
| Power                | Standard DC 5.5-2.5 and DC 5.5-2.1 compatible interface                                                                |
| DC pin 1             | VIN                                                                                                                    |
| DC pin 2             | GND                                                                                                                    |
| Standard accessories | AC1 sensor, 1 m screw-lock Type-C data cable, 1 m screw-lock DC power cord, 12 V 2 A DC adapter, product specification |

Use a USB 3.0-capable host port and avoid long or low-quality USB cables during initial validation. If the host does not enumerate the sensor, check power first, then USB link speed, then AC Viewer recognition.

## Software And Setup Workflow

AC Viewer is the primary RoboSense software for AC1. It displays Active Camera data, including point clouds and images, and can record/store sensor data for later use.

1. Connect the DC power cable and confirm the AC1 is powered.
2. Connect AC1 to the host PC through the screw-lock USB Type-C data cable.
3. Install or unzip AC Viewer on Windows 64-bit or Ubuntu 18.04 or later.
4. Keep the AC Viewer extraction path free of Chinese characters.
5. Open AC Viewer and select the connected AC1 device.
6. Confirm real-time point cloud, RGB image, and IMU data output.
7. Record a short data sample before integrating with your own software.

| PC item    | Minimum                                    | Recommended                                |
| ---------- | ------------------------------------------ | ------------------------------------------ |
| CPU        | 7th generation Intel Core i3 or equivalent | Intel 11500 or higher, or Mac M2 or higher |
| GPU        | Integrated graphics                        | NVIDIA RTX 3060 or above                   |
| RAM        | 8 GB                                       | 16 GB or higher                            |
| Connection | USB 3.0                                    | USB 3.0                                    |

## Communication Protocol

AC1 communicates with the host computer over USB 3.0 and outputs IMU, LiDAR, and image sensor data. The manual mentions LiDAR data structures including:

| Structure       | Purpose                                                                                    |
| --------------- | ------------------------------------------------------------------------------------------ |
| `cloud_point_t` | Point-level data such as x/y/z coordinates, reflectivity, and timestamp                    |
| `depth_frame_t` | Frame-level point-cloud data such as pixel width, height, image data format, and timestamp |

For software integration, validate the exact SDK or driver version against the hardware firmware before depending on field layouts in production code.

## Engineering Setup Checklist

| Check          | Expected result                                                                                   |
| -------------- | ------------------------------------------------------------------------------------------------- |
| Power adapter  | 12 V 2 A adapter connected                                                                        |
| USB link       | USB 3.0 / USB 3.2 Gen1 host connection                                                            |
| AC Viewer      | Opens without path/encoding issue                                                                 |
| Point cloud    | Real-time depth/point cloud visible                                                               |
| RGB image      | Image stream visible at expected resolution                                                       |
| IMU            | 6-axis data visible or recordable                                                                 |
| Revision check | Confirm AC1 manual/product naming because the source PDF includes an early `E1R User Guide` label |

## Best Practices And Limitations

* Use the manual values as integration baselines, but confirm final firmware and hardware revision before production design.
* Range and precision depend on target reflectivity, distance, ambient light, and environmental conditions.
* Use USB 3.0-quality cabling and a stable power source for repeatable data capture.
* Do not reuse RSView/Ethernet workflows from RoboSense Fairy or EM4; AC1 uses AC Viewer and USB.
* Confirm camera/IMU extrinsic calibration workflow from the official RoboSense AC Studio or documentation before sensor fusion.

## Troubleshooting

| Symptom                                  | Likely cause                                           | What to check                                                     |
| ---------------------------------------- | ------------------------------------------------------ | ----------------------------------------------------------------- |
| AC Viewer cannot see AC1                 | Power, USB cable, USB link speed, or host driver issue | Check DC power, use USB 3.0 port, change cable, restart AC Viewer |
| Point cloud is missing but image appears | Depth stream not enabled or driver mismatch            | Verify AC Viewer device settings and SDK/firmware compatibility   |
| Image stream drops frames                | Host performance or USB bandwidth issue                | Use recommended PC configuration and avoid USB hubs               |
| IMU data missing                         | Data channel not enabled or parser mismatch            | Confirm AC Viewer/SDK configuration and firmware version          |
| Range looks inconsistent                 | Reflectivity, lighting, or target-distance conditions  | Re-test with known targets and record environmental conditions    |

## Project References And Application Ideas

* Mobile robot obstacle detection using depth + RGB image streams.
* RGB-D perception datasets for indoor robotics.
* Visual-inertial experiments using AC1 RGB, depth, and IMU output.
* Object detection plus depth filtering for manipulation or navigation.
* USB sensor capture validation before ROS/ROS 2 integration.

## Resources

| Resource                 | Link                                                                   |
| ------------------------ | ---------------------------------------------------------------------- |
| OpenELAB product page    | https://openelab.io/products/robosense-ac1-lidar-depth-camera-pre-sale |
| RoboSense resources page | https://www.robosense.ai/en/resources                                  |
| Local manual source      | `AC1 .pdf`                                                             |
| Public CAD drawing       | Not found during this review                                           |
| Firmware package         | Not confirmed during this review                                       |
| SDK / AC Viewer          | Confirm the latest AC Viewer and SDK from official RoboSense resources |

## FAQ

<details>

<summary>Is RoboSense AC1 an Ethernet LiDAR?</summary>

No. AC1 uses USB 3.2 Gen1 / USB 3.0 data output. Use AC Viewer rather than RSView for first bring-up.

</details>

<details>

<summary>What data does AC1 output?</summary>

The manual describes LiDAR point cloud/depth data, RGB image data, and 6-axis IMU data.

</details>

<details>

<summary>What host computer should I use for AC1?</summary>

The manual lists a 7th generation Intel Core i3 or equivalent and 8 GB RAM as minimum. For smoother visualization, use an Intel 11500 or higher / Mac M2 or higher, NVIDIA RTX 3060 or above, and 16 GB RAM or more.

</details>

<details>

<summary>Why does the PDF mention E1R on early pages?</summary>

The source PDF contains an early `E1R User Guide` label while the main content identifies AC1. Treat this as a source-title inconsistency and confirm the final manual revision before production release.

</details>

## Source Notes

* Review date: 2026-06-04.
* Product source: OpenELAB product page and Shopify endpoint for `robosense-ac1-lidar-depth-camera-pre-sale`.
* Manual source: `AC1 .pdf`, manual version 1.0, revision dated 2025-04-11.
* Outbound link check: OpenELAB product page and RoboSense resources page were reachable during review.
* Excluded from this wiki: manufacturer email, phone, address, working hours, and support contact blocks from the source manual.
