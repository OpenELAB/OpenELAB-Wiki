---
description: >-
  A compact quadruped for ROS motion, balance, camera perception and optional
  LiDAR exercises.
---

# Hiwonder PuppyPi Guide

{% hint style="info" %}
[**View Hiwonder PuppyPi ROS AI Robot Dog Kit for Raspberry Pi 4B/5 on OpenELAB**](https://openelab.io/products/puppypi-ros)

**SKU:** `Hiwonder-21040065`, `Hiwonder-21040145`, `Hiwonder-21040067`, `Hiwonder-21040081`, `Hiwonder-21040089`, `Hiwonder-21040070`, `Hiwonder-21040146`, `Hiwonder-21040092`, `Hiwonder-21040093`, `Hiwonder-21040079`, `Hiwonder-21040095`, `Hiwonder-21040150`, `Hiwonder-21040097`, `Hiwonder-21040098`, `Hiwonder-21040099`, `Hiwonder-21040077`, `Hiwonder-21040148`, `Hiwonder-21040063`, `Hiwonder-21040066`, `Hiwonder-21040061`

**Model / revision scope:** PuppyPi. Match the purchased option below; hardware revisions and controller images are not interchangeable.
{% endhint %}

![PuppyPi — product image supplied by OpenELAB](../../.gitbook/assets/hiwonder-102.png)

## Product overview

A compact quadruped for ROS motion, balance, camera perception and optional LiDAR exercises.

The manufacturer’s shared connection text contains TurboPi labels; use this robot’s own app entry and model-specific control screen. Do not change the robot firmware to match the copied label.

### Models and purchasing options

| OpenELAB SKU        | Purchased option                              |
| ------------------- | --------------------------------------------- |
| `Hiwonder-21040065` | Standard Kit / With Raspberry Pi 4B (4GB)     |
| `Hiwonder-21040145` | Standard Kit / With Raspberry Pi 5 (2GB)      |
| `Hiwonder-21040067` | Standard Kit / With Raspberry Pi 5 (4GB)      |
| `Hiwonder-21040081` | Standard Kit / With Raspberry Pi 5 (8GB)      |
| `Hiwonder-21040089` | Standard Kit / With Raspberry Pi 5 (16GB)     |
| `Hiwonder-21040070` | Advanced Kit / With Raspberry Pi 4B (4GB)     |
| `Hiwonder-21040146` | Advanced Kit / With Raspberry Pi 5 (2GB)      |
| `Hiwonder-21040092` | Advanced Kit / With Raspberry Pi 5 (4GB)      |
| `Hiwonder-21040093` | Advanced Kit / With Raspberry Pi 5 (8GB)      |
| `Hiwonder-21040079` | Advanced Kit / With Raspberry Pi 5 (16GB)     |
| `Hiwonder-21040095` | Pro Kit / With Raspberry Pi 4B (4GB)          |
| `Hiwonder-21040150` | Pro Kit / With Raspberry Pi 5 (2GB)           |
| `Hiwonder-21040097` | Pro Kit / With Raspberry Pi 5 (4GB)           |
| `Hiwonder-21040098` | Pro Kit / With Raspberry Pi 5 (8GB)           |
| `Hiwonder-21040099` | Pro Kit / With Raspberry Pi 5 (16GB)          |
| `Hiwonder-21040077` | Pro Ultimate Kit / With Raspberry Pi 4B (4GB) |
| `Hiwonder-21040148` | Pro Ultimate Kit / With Raspberry Pi 5 (2GB)  |
| `Hiwonder-21040063` | Pro Ultimate Kit / With Raspberry Pi 5 (4GB)  |
| `Hiwonder-21040066` | Pro Ultimate Kit / With Raspberry Pi 5 (8GB)  |
| `Hiwonder-21040061` | Pro Ultimate Kit / With Raspberry Pi 5 (16GB) |

## Applications

Use PuppyPi to learn joint coordination, gait/pose control and camera-based interaction.

## Specifications

| Parameter         | Value / scope                                                           |
| ----------------- | ----------------------------------------------------------------------- |
| Controller        | Raspberry Pi option in the SKU table; Pi 4 and Pi 5 images differ       |
| Battery reference | 7.4 V, 2200 mAh                                                         |
| Mechanism         | Quadruped; match the purchased arm/LiDAR option                         |
| Mass reference    | Approximately 720 g base configuration                                  |
| Software          | Model-specific image; ROS generation depends on purchased configuration |

Specifications: [manufacturer product data](https://www.hiwonder.com/products/puppypi) and [OpenELAB listing](https://openelab.io/products/puppypi-ros). Figures describe the stated configuration; accessory-only options do not inherit the complete kit specifications.

## Hardware and connections

Connect the supplied battery or adapter to the **robot’s designated power/expansion board**, not directly to a computer GPIO or an unverified charging socket. Inspect the camera, motor/servo and controller cables while power is off. Keep a clear area around every leg and support the robot in the initial resting posture shown in its model manual. Do not hold a powered joint by hand.

Match the controller, camera, LiDAR and chassis configuration to the SKU. Optional voice/AI modules require their own cables and software. A USB camera, depth camera and CSI ribbon camera are not interchangeable interfaces.

## Software and development resources

Start with the factory image for **PuppyPi and the exact controller option**. WonderPi is the documented initial control application. Use the official model downloads for restoration; a generic Raspberry Pi OS or JetPack installation does not include the robot services, calibrated offsets and device configuration.

For development, preserve a backup of the supplied image and calibration files before replacing software. Select the manual branch for the installed board and ROS generation. A menu or directory for a different product is not a compatible firmware target.

## Getting started

**Prerequisites:** the selected hardware, its matching power source, the required data cable, and a clear work area. Begin with the supplied firmware and an unloaded mechanism.

1. Match the SKU table to the physical controller and kit. For a controller-excluded option, install the supported board and its exact robot image before attempting the remaining steps.
2. Keep a clear area around every leg and support the robot in the initial resting posture shown in its model manual. Do not hold a powered joint by hand. Inspect polarity and cable seating, then power the robot with the supplied matching power system.
3. Allow the onboard computer to finish booting and reach its documented ready posture/indicator state. Keep the mechanism clear because initialization may move servos.
4. Install **WonderPi** from the model’s official resources. Enable Wi-Fi and the local-network/location permissions required for discovery. Select **PuppyPi**, then **+ → Direct Connection Mode**.
5. Join the robot’s **HW…** hotspot using **hiwonder** on an unchanged factory image. Stay connected if the phone reports no Internet; return to the app and refresh until the correct robot icon appears.
6. Open the model’s Robot/Remote Control screen and verify the camera feed before issuing a brief low-speed command on a clear floor. Release the control and verify the robot stops; avoid autonomous gaits for this first test.
7. End the demonstration and shut down the onboard operating system before removing power. Keep the original image and configuration until basic control is repeatable.

**Expected result:** The correct robot is discovered, its live camera/connection status is visible, and one small manual command responds and stops predictably. Autonomous tasks and loaded motion remain subsequent tests.

Procedure reference: [official model or interface manual](https://wiki.hiwonder.com/projects/PuppyPi/en/latest/docs/2.Quick_User_Experience.html). The steps above are a bounded initial check, not a substitute for the full assembly and development chapters.

## Troubleshooting and FAQs

**No hotspot:** wait for the full boot sequence, verify the battery/adapter and image/controller match, then check whether the robot was previously configured for LAN mode.

**Phone joins Wi-Fi but the app sees nothing:** remain on the robot network despite the no-Internet warning, grant local-network discovery permissions, select the correct model and refresh. The factory password may have been changed on a used unit.

**Camera works but motion is wrong:** stop immediately and verify the chassis type, motor/servo connections and model configuration. Do not compensate with unrelated servo offsets.

**Vision, mapping or voice option is unavailable:** check the selected kit’s actual camera, LiDAR and AI/voice modules. Offline local control does not establish that a cloud AI service is configured.

**Restoring firmware:** use the exact model/controller resource package and retain calibration files; do not write an image for a similarly named Pro or legacy version.

## Downloads and technical documents

* [Official user / interface manual](https://wiki.hiwonder.com/projects/PuppyPi/en/latest/docs/2.Quick_User_Experience.html)
* [Official software, image and course downloads](https://wiki.hiwonder.com/projects/PuppyPi/en/latest/docs/resources_download.html)
* [Startup posture, power and charging](https://wiki.hiwonder.com/projects/PuppyPi/en/latest/docs/1.Quick_Start_Guide.html)
* [Manufacturer Hiwonder PuppyPi ROS AI Robot Dog Kit for Raspberry Pi 4B/5 specifications and option drawings](https://www.hiwonder.com/products/puppypi)

Use the manual’s download or appendix section for the matching revision. A linked download directory is not a claim that every firmware archive, CAD file or installer has been tested. Do not flash an image for a similarly named product.

## References and validation

* [OpenELAB product and SKU options](https://openelab.io/products/puppypi-ros).
* [Official user / interface manual](https://wiki.hiwonder.com/projects/PuppyPi/en/latest/docs/2.Quick_User_Experience.html)
* [Official software, image and course downloads](https://wiki.hiwonder.com/projects/PuppyPi/en/latest/docs/resources_download.html)
* [Startup posture, power and charging](https://wiki.hiwonder.com/projects/PuppyPi/en/latest/docs/1.Quick_Start_Guide.html)
* [Manufacturer Hiwonder PuppyPi ROS AI Robot Dog Kit for Raspberry Pi 4B/5 specifications and option drawings](https://www.hiwonder.com/products/puppypi)

Reviewed against the linked sources on 19 November 2026. Software installation, compilation and physical hardware tests were not performed for this guide. Use the observable checkpoints above to verify your own unit before integrating it into a larger system.
