---
description: >-
  JetAcker uses Ackermann steering for vehicle-like robotics development. Its
  steering geometry differs from Mecanum and tank-drive robots even when the
  controller and ROS tools look similar.
---

# Hiwonder JetAcker Guide

{% hint style="info" %}
[**View Hiwonder JetAcker ROS Robot Kit with Jetson/Raspberry Pi, LiDAR, 3D Vision & SLAM on OpenELAB**](https://openelab.io/products/jetacker-ai-robot-kit)

**SKU:** `Hiwonder-21030725`, `Hiwonder-21030843`, `Hiwonder-21030726`, `Hiwonder-21030727`, `Hiwonder-21030728`, `Hiwonder-21030729`, `Hiwonder-21030730`, `Hiwonder-21030731`, `Hiwonder-21030844`, `Hiwonder-21030732`, `Hiwonder-21030733`, `Hiwonder-21030734`, `Hiwonder-21030735`, `Hiwonder-21030736`, `Hiwonder-21030737`, `Hiwonder-21030917`, `Hiwonder-21030738`, `Hiwonder-21030739`, `Hiwonder-21030740`, `Hiwonder-21030741`, `Hiwonder-21030742`, `Hiwonder-21030743`, `Hiwonder-21030918`, `Hiwonder-21030744`, `Hiwonder-21030745`, `Hiwonder-21030746`, `Hiwonder-21030498`, `Hiwonder-21030747`

**Model / revision scope:** JetAcker. Match the purchased option below; hardware revisions and controller images are not interchangeable.
{% endhint %}

![JetAcker — product image supplied by OpenELAB](../../.gitbook/assets/hiwonder-84.png)

## Product overview

JetAcker uses Ackermann steering for vehicle-like robotics development. Its steering geometry differs from Mecanum and tank-drive robots even when the controller and ROS tools look similar.

Before driving, verify the steering assembly is free and the configured chassis is Ackermann. A Mecanum motion program is not a substitute for this vehicle’s kinematics.

### Models and purchasing options

| OpenELAB SKU        | Purchased option                                |
| ------------------- | ----------------------------------------------- |
| `Hiwonder-21030725` | Starter Kit / Without Controller                |
| `Hiwonder-21030843` | Starter Kit / With Raspberry Pi 5(8GB)          |
| `Hiwonder-21030726` | Starter Kit / With Jetson Nano(4GB)             |
| `Hiwonder-21030727` | Starter Kit / With Jetson Orin Nano Super(4GB)  |
| `Hiwonder-21030728` | Starter Kit / With Jetson Orin Nano Super(8GB)  |
| `Hiwonder-21030729` | Starter Kit / With Jetson Orin NX Super(8GB)    |
| `Hiwonder-21030730` | Starter Kit / With Jetson Orin NX Super(16GB)   |
| `Hiwonder-21030731` | Standard Kit / Without Controller               |
| `Hiwonder-21030844` | Standard Kit / With Raspberry Pi 5(8GB)         |
| `Hiwonder-21030732` | Standard Kit / With Jetson Nano(4GB)            |
| `Hiwonder-21030733` | Standard Kit / With Jetson Orin Nano Super(4GB) |
| `Hiwonder-21030734` | Standard Kit / With Jetson Orin Nano Super(8GB) |
| `Hiwonder-21030735` | Standard Kit / With Jetson Orin NX Super(8GB)   |
| `Hiwonder-21030736` | Standard Kit / With Jetson Orin NX Super(16GB)  |
| `Hiwonder-21030737` | Advanced Kit / Without Controller               |
| `Hiwonder-21030917` | Advanced Kit / With Raspberry Pi 5(8GB)         |
| `Hiwonder-21030738` | Advanced Kit / With Jetson Nano(4GB)            |
| `Hiwonder-21030739` | Advanced Kit / With Jetson Orin Nano Super(4GB) |
| `Hiwonder-21030740` | Advanced Kit / With Jetson Orin Nano Super(8GB) |
| `Hiwonder-21030741` | Advanced Kit / With Jetson Orin NX Super(8GB)   |
| `Hiwonder-21030742` | Advanced Kit / With Jetson Orin NX Super(16GB)  |
| `Hiwonder-21030743` | Ultimate Kit / Without Controller               |
| `Hiwonder-21030918` | Ultimate Kit / With Raspberry Pi 5(8GB)         |
| `Hiwonder-21030744` | Ultimate Kit / With Jetson Nano(4GB)            |
| `Hiwonder-21030745` | Ultimate Kit / With Jetson Orin Nano Super(4GB) |
| `Hiwonder-21030746` | Ultimate Kit / With Jetson Orin Nano Super(8GB) |
| `Hiwonder-21030498` | Ultimate Kit / With Jetson Orin NX Super(8GB)   |
| `Hiwonder-21030747` | Ultimate Kit / With Jetson Orin NX Super(16GB)  |

A separately named bracket, horn, chassis or rail is the listed accessory, not a complete robot or servo. A “without controller / Raspberry Pi / Jetson / micro:bit” option requires the matching controller separately. Check the selected option’s packing list before starting.

## Applications

Use JetAcker to learn manual motion, perception and staged automation. Start with an unloaded mechanism and the sensors actually included in the selected kit.

## Specifications

| Parameter         | Value / scope                                |
| ----------------- | -------------------------------------------- |
| Drive             | Ackermann steering with encoder drive        |
| Controller        | Exact Jetson / Raspberry Pi option as listed |
| Sensors           | Camera, LiDAR, voice/display vary by kit     |
| Operating system  | Match the model-specific controller image    |
| Motion constraint | No sideways translation                      |

Specifications: [manufacturer product data](https://www.hiwonder.com/products/jetacker) and [OpenELAB listing](https://openelab.io/products/jetacker-ai-robot-kit). Figures describe the stated configuration; accessory-only options do not inherit the complete kit specifications.

## Hardware and connections

Connect the supplied battery or adapter to the **robot’s designated power/expansion board**, not directly to a computer GPIO or an unverified charging socket. Inspect the camera, motor/servo and controller cables while power is off. Place the mobile base on a clear level floor, away from edges, and remove objects from any gripper.

Match the controller, camera, LiDAR and chassis configuration to the SKU. Optional voice/AI modules require their own cables and software. A USB camera, depth camera and CSI ribbon camera are not interchangeable interfaces.

## Software and development resources

Start with the factory image for **JetAcker and the exact controller option**. WonderAi is the documented initial control application. Use the official model downloads for restoration; a generic Raspberry Pi OS or JetPack installation does not include the robot services, calibrated offsets and device configuration.

For development, preserve a backup of the supplied image and calibration files before replacing software. Select the manual branch for the installed board and ROS generation. A menu or directory for a different product is not a compatible firmware target.

## Getting started

**Prerequisites:** the selected hardware, its matching power source, the required data cable, and a clear work area. Begin with the supplied firmware and an unloaded mechanism.

1. Match the SKU table to the physical controller and kit. For a controller-excluded option, install the supported board and its exact robot image before attempting the remaining steps.
2. Place the mobile base on a clear level floor, away from edges, and remove objects from any gripper. Inspect polarity and cable seating, then power the robot with the supplied matching power system.
3. Allow the onboard computer to finish booting and reach its documented ready posture/indicator state. Keep the mechanism clear because initialization may move servos.
4. Install **WonderAi** from the model’s official resources. Enable Wi-Fi and the local-network/location permissions required for discovery. Select **Advanced → JetAcker**, then **+ → Direct Connection Mode**.
5. Join the robot’s **HW…** hotspot using **hiwonder** on an unchanged factory image. Stay connected if the phone reports no Internet; return to the app and refresh until the correct robot icon appears.
6. Open Robot/Remote Control and verify the camera image. Give a brief low-speed forward command, release it and confirm the base stops before testing a turn.
7. End the demonstration and shut down the onboard operating system before removing power. Keep the original image and configuration until basic control is repeatable.

**Expected result:** The correct robot is discovered, its live camera/connection status is visible, and one small manual command responds and stops predictably. Autonomous tasks and loaded motion remain subsequent tests.

Procedure reference: [official model or interface manual](https://wiki.hiwonder.com/projects/JetAcker/en/jetacker-orin-nano/docs/1.getting_ready.html). The steps above are a bounded initial check, not a substitute for the full assembly and development chapters.

## Troubleshooting and FAQs

**No hotspot:** wait for the full boot sequence, verify the battery/adapter and image/controller match, then check whether the robot was previously configured for LAN mode.

**Phone joins Wi-Fi but the app sees nothing:** remain on the robot network despite the no-Internet warning, grant local-network discovery permissions, select the correct model and refresh. The factory password may have been changed on a used unit.

**Camera works but motion is wrong:** stop immediately and verify the chassis type, motor/servo connections and model configuration. Do not compensate with unrelated servo offsets.

**Vision, mapping or voice option is unavailable:** check the selected kit’s actual camera, LiDAR and AI/voice modules. Offline local control does not establish that a cloud AI service is configured.

**Restoring firmware:** use the exact model/controller resource package and retain calibration files; do not write an image for a similarly named Pro or legacy version.

## Downloads and technical documents

* [Official user / interface manual](https://wiki.hiwonder.com/projects/JetAcker/en/jetacker-orin-nano/docs/1.getting_ready.html)
* [Official software, image and course downloads](https://wiki.hiwonder.com/projects/JetAcker/en/jetacker-orin-nano/docs/resources_download.html)
* [Manufacturer Hiwonder JetAcker ROS Robot Kit with Jetson/Raspberry Pi, LiDAR, 3D Vision & SLAM specifications and option drawings](https://www.hiwonder.com/products/jetacker)

Use the manual’s download or appendix section for the matching revision. A linked download directory is not a claim that every firmware archive, CAD file or installer has been tested. Do not flash an image for a similarly named product.

## References and validation

* [OpenELAB product and SKU options](https://openelab.io/products/jetacker-ai-robot-kit).
* [Official user / interface manual](https://wiki.hiwonder.com/projects/JetAcker/en/jetacker-orin-nano/docs/1.getting_ready.html)
* [Official software, image and course downloads](https://wiki.hiwonder.com/projects/JetAcker/en/jetacker-orin-nano/docs/resources_download.html)
* [Manufacturer Hiwonder JetAcker ROS Robot Kit with Jetson/Raspberry Pi, LiDAR, 3D Vision & SLAM specifications and option drawings](https://www.hiwonder.com/products/jetacker)

Reviewed against the linked sources on 19 November 2026. Software installation, compilation and physical hardware tests were not performed for this guide. Use the observable checkpoints above to verify your own unit before integrating it into a larger system.
