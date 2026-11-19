---
description: >-
  JetAuto Pro adds a manipulator to the JetAuto mobile platform for
  vision-guided transport. The mobile base and arm must both be configured for
  the selected kit before coordinated tasks.
---

# Hiwonder JetAuto Pro Guide

{% hint style="info" %}
[**View Hiwonder JetAuto Pro ROS2 Mobile Manipulator with 6DOF Arm & LiDAR SLAM on OpenELAB**](https://openelab.io/products/hiwonder-jetauto-pro-ai-car)

**SKU:** `Hiwonder-21030780`, `Hiwonder-21030781`, `Hiwonder-21030782`, `Hiwonder-21030783`, `Hiwonder-21030784`, `Hiwonder-21030802`, `Hiwonder-21030803`, `Hiwonder-21030779`, `Hiwonder-21030804`, `Hiwonder-21030670`, `Hiwonder-21030805`, `Hiwonder-21030806`, `Hiwonder-21030807`, `Hiwonder-21030808`, `Hiwonder-21030809`, `Hiwonder-21030810`, `Hiwonder-21030666`

**Model / revision scope:** JetAuto Pro. Match the purchased option below; hardware revisions and controller images are not interchangeable.
{% endhint %}

![JetAuto Pro — product image supplied by OpenELAB](../../.gitbook/assets/hiwonder-20.png)

## Product overview

JetAuto Pro adds a manipulator to the JetAuto mobile platform for vision-guided transport. The mobile base and arm must both be configured for the selected kit before coordinated tasks.

The official configuration utility distinguishes JetAuto and JetAutoPro. Check camera, LiDAR and Machine selections; use Save → Apply → Quit only when correcting a confirmed mismatch.

### Models and purchasing options

| OpenELAB SKU        | Purchased option                                |
| ------------------- | ----------------------------------------------- |
| `Hiwonder-21030780` | Standard Kit / Without Controller               |
| `Hiwonder-21030781` | Standard Kit / With Raspberry Pi 5(8GB)         |
| `Hiwonder-21030782` | Standard Kit / With Jetson Nano(4GB)            |
| `Hiwonder-21030783` | Standard Kit / With Jetson Orin Nano Super(4GB) |
| `Hiwonder-21030784` | Standard Kit / With Jetson Orin Nano Super(8GB) |
| `Hiwonder-21030802` | Advanced Kit / Without Controller               |
| `Hiwonder-21030803` | Advanced Kit / With Raspberry Pi 5(8GB)         |
| `Hiwonder-21030779` | Advanced Kit / With Jetson Nano(4GB)            |
| `Hiwonder-21030804` | Advanced Kit / With Jetson Orin Nano Super(4GB) |
| `Hiwonder-21030670` | Advanced Kit / With Jetson Orin Nano Super(8GB) |
| `Hiwonder-21030805` | Ultimate Kit / Without Controller               |
| `Hiwonder-21030806` | Ultimate Kit / With Raspberry Pi 5(8GB)         |
| `Hiwonder-21030807` | Ultimate Kit / With Jetson Nano(4GB)            |
| `Hiwonder-21030808` | Ultimate Kit / With Jetson Orin Nano Super(4GB) |
| `Hiwonder-21030809` | Ultimate Kit / With Jetson Orin Nano Super(8GB) |
| `Hiwonder-21030810` | Ultimate Kit / With Jetson Orin NX Super(8GB)   |
| `Hiwonder-21030666` | Ultimate Kit / With Jetson Orin NX Super(16GB)  |

A separately named bracket, horn, chassis or rail is the listed accessory, not a complete robot or servo. A “without controller / Raspberry Pi / Jetson / micro:bit” option requires the matching controller separately. Check the selected option’s packing list before starting.

## Applications

Use JetAuto Pro to learn manual motion, perception and staged automation. Start with an unloaded mechanism and the sensors actually included in the selected kit.

## Specifications

| Parameter        | Value / scope                                 |
| ---------------- | --------------------------------------------- |
| Drive            | Mecanum encoder-motor base                    |
| Arm              | Vision robotic arm, Pro configuration         |
| Battery          | 11.1 V, 6000 mAh listed pack                  |
| Mass reference   | Approximately 4.8 kg, configuration-dependent |
| Controller / ROS | Match Jetson or Raspberry Pi option and image |

Specifications: [manufacturer product data](https://www.hiwonder.com/products/jetauto-pro) and [OpenELAB listing](https://openelab.io/products/hiwonder-jetauto-pro-ai-car). Figures describe the stated configuration; accessory-only options do not inherit the complete kit specifications.

## Hardware and connections

Connect the supplied battery or adapter to the **robot’s designated power/expansion board**, not directly to a computer GPIO or an unverified charging socket. Inspect the camera, motor/servo and controller cables while power is off. Place the mobile base on a clear level floor, away from edges, and remove objects from any gripper.

Match the controller, camera, LiDAR and chassis configuration to the SKU. Optional voice/AI modules require their own cables and software. A USB camera, depth camera and CSI ribbon camera are not interchangeable interfaces.

## Software and development resources

Start with the factory image for **JetAuto Pro and the exact controller option**. WonderAi is the documented initial control application. Use the official model downloads for restoration; a generic Raspberry Pi OS or JetPack installation does not include the robot services, calibrated offsets and device configuration.

For development, preserve a backup of the supplied image and calibration files before replacing software. Select the manual branch for the installed board and ROS generation. A menu or directory for a different product is not a compatible firmware target.

## Getting started

**Prerequisites:** the selected hardware, its matching power source, the required data cable, and a clear work area. Begin with the supplied firmware and an unloaded mechanism.

1. Match the SKU table to the physical controller and kit. For a controller-excluded option, install the supported board and its exact robot image before attempting the remaining steps.
2. Place the mobile base on a clear level floor, away from edges, and remove objects from any gripper. Inspect polarity and cable seating, then power the robot with the supplied matching power system.
3. Allow the onboard computer to finish booting and reach its documented ready posture/indicator state. Keep the mechanism clear because initialization may move servos.
4. Install **WonderAi** from the model’s official resources. Enable Wi-Fi and the local-network/location permissions required for discovery. Select **Advanced → JetAuto Pro**, then **+ → Direct Connection Mode**.
5. Join the robot’s **HW…** hotspot using **hiwonder** on an unchanged factory image. Stay connected if the phone reports no Internet; return to the app and refresh until the correct robot icon appears.
6. Open Robot/Remote Control and verify the camera image. Give a brief low-speed forward command, release it and confirm the base stops before testing a turn.
7. End the demonstration and shut down the onboard operating system before removing power. Keep the original image and configuration until basic control is repeatable.

**Expected result:** The correct robot is discovered, its live camera/connection status is visible, and one small manual command responds and stops predictably. Autonomous tasks and loaded motion remain subsequent tests.

Procedure reference: [official model or interface manual](https://wiki.hiwonder.com/projects/JetAuto/en/jetauto-orin-nano/docs/1.quick_start_guide.html). The steps above are a bounded initial check, not a substitute for the full assembly and development chapters.

## Troubleshooting and FAQs

**No hotspot:** wait for the full boot sequence, verify the battery/adapter and image/controller match, then check whether the robot was previously configured for LAN mode.

**Phone joins Wi-Fi but the app sees nothing:** remain on the robot network despite the no-Internet warning, grant local-network discovery permissions, select the correct model and refresh. The factory password may have been changed on a used unit.

**Camera works but motion is wrong:** stop immediately and verify the chassis type, motor/servo connections and model configuration. Do not compensate with unrelated servo offsets.

**Vision, mapping or voice option is unavailable:** check the selected kit’s actual camera, LiDAR and AI/voice modules. Offline local control does not establish that a cloud AI service is configured.

**Restoring firmware:** use the exact model/controller resource package and retain calibration files; do not write an image for a similarly named Pro or legacy version.

## Downloads and technical documents

* [Official user / interface manual](https://wiki.hiwonder.com/projects/JetAuto/en/jetauto-orin-nano/docs/1.quick_start_guide.html)
* [Official software, image and course downloads](https://wiki.hiwonder.com/projects/JetAuto/en/jetauto-orin-nano/docs/resources_download.html)
* [Manufacturer Hiwonder JetAuto Pro ROS2 Mobile Manipulator with 6DOF Arm & LiDAR SLAM specifications and option drawings](https://www.hiwonder.com/products/jetauto-pro)

Use the manual’s download or appendix section for the matching revision. A linked download directory is not a claim that every firmware archive, CAD file or installer has been tested. Do not flash an image for a similarly named product.

## References and validation

* [OpenELAB product and SKU options](https://openelab.io/products/hiwonder-jetauto-pro-ai-car).
* [Official user / interface manual](https://wiki.hiwonder.com/projects/JetAuto/en/jetauto-orin-nano/docs/1.quick_start_guide.html)
* [Official software, image and course downloads](https://wiki.hiwonder.com/projects/JetAuto/en/jetauto-orin-nano/docs/resources_download.html)
* [Manufacturer Hiwonder JetAuto Pro ROS2 Mobile Manipulator with 6DOF Arm & LiDAR SLAM specifications and option drawings](https://www.hiwonder.com/products/jetauto-pro)

Reviewed against the linked sources on 19 November 2026. Software installation, compilation and physical hardware tests were not performed for this guide. Use the observable checkpoints above to verify your own unit before integrating it into a larger system.
