---
description: >-
  MentorPi T1 is the tracked member of the MentorPi ROS2 family. The controller,
  camera, LiDAR and learning-kit options in this listing determine which
  demonstrations can run.
---

# Hiwonder MentorPi T1 Guide

{% hint style="info" %}
[**View Hiwonder MentorPi T1 ROS2 Tank AI Robot Car Kit for Raspberry Pi 5 on OpenELAB**](https://openelab.io/products/hiwonder-mentorpi-t1-ros2-tank)

**SKU:** `Hiwonder-21030953`, `Hiwonder-21031931`, `Hiwonder-21030954`, `Hiwonder-21030955`, `Hiwonder-21030956`, `Hiwonder-21030951`, `Hiwonder-21031934`, `Hiwonder-21030909`, `Hiwonder-21030910`, `Hiwonder-21030911`, `Hiwonder-21030952`, `Hiwonder-21031937`, `Hiwonder-21030957`, `Hiwonder-21030958`, `Hiwonder-21031199`

**Model / revision scope:** MentorPi T1. Match the purchased option below; hardware revisions and controller images are not interchangeable.
{% endhint %}

![MentorPi T1 — product image supplied by OpenELAB](../../.gitbook/assets/hiwonder-92.png)

## Product overview

MentorPi T1 is the tracked member of the MentorPi ROS2 family. The controller, camera, LiDAR and learning-kit options in this listing determine which demonstrations can run.

Select the exact T1 chassis profile before movement. Motor direction and wheel/track arrangement must agree with the configured geometry.

### Models and purchasing options

| OpenELAB SKU        | Purchased option                    |
| ------------------- | ----------------------------------- |
| `Hiwonder-21030953` | Starter / Without Raspberry Pi 5    |
| `Hiwonder-21031931` | Starter / With Raspberry Pi 5 2GB   |
| `Hiwonder-21030954` | Starter / With Raspberry Pi 5 4GB   |
| `Hiwonder-21030955` | Starter / With Raspberry Pi 5 8GB   |
| `Hiwonder-21030956` | Starter / With Raspberry Pi 5 16GB  |
| `Hiwonder-21030951` | Standard / Without Raspberry Pi 5   |
| `Hiwonder-21031934` | Standard / With Raspberry Pi 5 2GB  |
| `Hiwonder-21030909` | Standard / With Raspberry Pi 5 4GB  |
| `Hiwonder-21030910` | Standard / With Raspberry Pi 5 8GB  |
| `Hiwonder-21030911` | Standard / With Raspberry Pi 5 16GB |
| `Hiwonder-21030952` | Advanced / Without Raspberry Pi 5   |
| `Hiwonder-21031937` | Advanced / With Raspberry Pi 5 2GB  |
| `Hiwonder-21030957` | Advanced / With Raspberry Pi 5 4GB  |
| `Hiwonder-21030958` | Advanced / With Raspberry Pi 5 8GB  |
| `Hiwonder-21031199` | Advanced / With Raspberry Pi 5 16GB |

A separately named bracket, horn, chassis or rail is the listed accessory, not a complete robot or servo. A “without controller / Raspberry Pi / Jetson / micro:bit” option requires the matching controller separately. Check the selected option’s packing list before starting.

## Applications

Use MentorPi T1 to learn manual motion, perception and staged automation. Start with an unloaded mechanism and the sensors actually included in the selected kit.

## Specifications

| Parameter      | Value / scope                                             |
| -------------- | --------------------------------------------------------- |
| Controller     | Raspberry Pi 5 option; check inclusion and RAM            |
| Drive geometry | Tracked                                                   |
| Sensors        | Camera / LiDAR vary with purchased kit                    |
| Robot image    | Matching MentorPi T1 image                                |
| Power          | Supplied battery/charger matched to the physical revision |

Specifications: [manufacturer product data](https://www.hiwonder.com/products/mentorpi-t1) and [OpenELAB listing](https://openelab.io/products/hiwonder-mentorpi-t1-ros2-tank). Figures describe the stated configuration; accessory-only options do not inherit the complete kit specifications.

## Hardware and connections

Connect the supplied battery or adapter to the **robot’s designated power/expansion board**, not directly to a computer GPIO or an unverified charging socket. Inspect the camera, motor/servo and controller cables while power is off. Place the mobile base on a clear level floor, away from edges, and remove objects from any gripper.

Match the controller, camera, LiDAR and chassis configuration to the SKU. Optional voice/AI modules require their own cables and software. A USB camera, depth camera and CSI ribbon camera are not interchangeable interfaces.

## Software and development resources

Start with the factory image for **MentorPi T1 and the exact controller option**. WonderPi is the documented initial control application. Use the official model downloads for restoration; a generic Raspberry Pi OS or JetPack installation does not include the robot services, calibrated offsets and device configuration.

For development, preserve a backup of the supplied image and calibration files before replacing software. Select the manual branch for the installed board and ROS generation. A menu or directory for a different product is not a compatible firmware target.

## Getting started

**Prerequisites:** the selected hardware, its matching power source, the required data cable, and a clear work area. Begin with the supplied firmware and an unloaded mechanism.

1. Match the SKU table to the physical controller and kit. For a controller-excluded option, install the supported board and its exact robot image before attempting the remaining steps.
2. Place the mobile base on a clear level floor, away from edges, and remove objects from any gripper. Inspect polarity and cable seating, then power the robot with the supplied matching power system.
3. Allow the onboard computer to finish booting and reach its documented ready posture/indicator state. Keep the mechanism clear because initialization may move servos.
4. Install **WonderPi** from the model’s official resources. Enable Wi-Fi and the local-network/location permissions required for discovery. Select **Advanced → MentorPi-T1**, then **+ → Direct Connection Mode**.
5. Join the robot’s **HW…** hotspot using **hiwonder** on an unchanged factory image. Stay connected if the phone reports no Internet; return to the app and refresh until the correct robot icon appears.
6. Open Robot/Remote Control and verify the camera image. Give a brief low-speed forward command, release it and confirm the base stops before testing a turn.
7. End the demonstration and shut down the onboard operating system before removing power. Keep the original image and configuration until basic control is repeatable.

**Expected result:** The correct robot is discovered, its live camera/connection status is visible, and one small manual command responds and stops predictably. Autonomous tasks and loaded motion remain subsequent tests.

Procedure reference: [official model or interface manual](https://wiki.hiwonder.com/projects/MentorPi-T1/en/latest/docs/1.getting_ready.html). The steps above are a bounded initial check, not a substitute for the full assembly and development chapters.

## Troubleshooting and FAQs

**No hotspot:** wait for the full boot sequence, verify the battery/adapter and image/controller match, then check whether the robot was previously configured for LAN mode.

**Phone joins Wi-Fi but the app sees nothing:** remain on the robot network despite the no-Internet warning, grant local-network discovery permissions, select the correct model and refresh. The factory password may have been changed on a used unit.

**Camera works but motion is wrong:** stop immediately and verify the chassis type, motor/servo connections and model configuration. Do not compensate with unrelated servo offsets.

**Vision, mapping or voice option is unavailable:** check the selected kit’s actual camera, LiDAR and AI/voice modules. Offline local control does not establish that a cloud AI service is configured.

**Restoring firmware:** use the exact model/controller resource package and retain calibration files; do not write an image for a similarly named Pro or legacy version.

## Downloads and technical documents

* [Official user / interface manual](https://wiki.hiwonder.com/projects/MentorPi-T1/en/latest/docs/1.getting_ready.html)
* [Official software, image and course downloads](https://wiki.hiwonder.com/projects/MentorPi-T1/en/latest/docs/resources_download.html)
* [Manufacturer Hiwonder MentorPi T1 ROS2 Tank AI Robot Car Kit for Raspberry Pi 5 specifications and option drawings](https://www.hiwonder.com/products/mentorpi-t1)

Use the manual’s download or appendix section for the matching revision. A linked download directory is not a claim that every firmware archive, CAD file or installer has been tested. Do not flash an image for a similarly named product.

## References and validation

* [OpenELAB product and SKU options](https://openelab.io/products/hiwonder-mentorpi-t1-ros2-tank).
* [Official user / interface manual](https://wiki.hiwonder.com/projects/MentorPi-T1/en/latest/docs/1.getting_ready.html)
* [Official software, image and course downloads](https://wiki.hiwonder.com/projects/MentorPi-T1/en/latest/docs/resources_download.html)
* [Manufacturer Hiwonder MentorPi T1 ROS2 Tank AI Robot Car Kit for Raspberry Pi 5 specifications and option drawings](https://www.hiwonder.com/products/mentorpi-t1)

Reviewed against the linked sources on 19 November 2026. Software installation, compilation and physical hardware tests were not performed for this guide. Use the observable checkpoints above to verify your own unit before integrating it into a larger system.
