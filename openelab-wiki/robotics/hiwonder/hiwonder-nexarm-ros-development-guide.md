---
description: >-
  NexArm ROS pairs the NexArm manipulator with a supported ROS host for 3D
  perception and robot-arm development. This guide is separate from the
  ESP32/leader-follower NexArm options.
---

# Hiwonder NexArm ROS Guide

{% hint style="info" %}
[**View Hiwonder NexArm ROS VLA AI Robotic Arm Kit with Jetson/Raspberry Pi Options on OpenELAB**](https://openelab.io/products/hiwonder-nexarm-ros-robotic-arm)

**SKU:** `Hiwonder-21010731`, `Hiwonder-21010732`, `Hiwonder-21010733`, `Hiwonder-21010734`, `Hiwonder-21010797`, `Hiwonder-21010735`, `Hiwonder-21010736`, `Hiwonder-21010737`, `Hiwonder-21010738`, `Hiwonder-21010739`

**Model / revision scope:** NexArm ROS. Match the purchased option below; hardware revisions and controller images are not interchangeable.
{% endhint %}

![NexArm ROS — product image supplied by OpenELAB](../../.gitbook/assets/hiwonder-16.jpg)

## Product overview

NexArm ROS pairs the NexArm manipulator with a supported ROS host for 3D perception and robot-arm development. This guide is separate from the ESP32/leader-follower NexArm options.

Secure a stand-alone arm with the supplied G clamps, or fasten the base to the sandbox assembly as documented. A leader arm, imitation-learning camera set or ROS host is included only when the selected option says so.

### Models and purchasing options

| OpenELAB SKU        | Purchased option                 |
| ------------------- | -------------------------------- |
| `Hiwonder-21010731` | Without Controller               |
| `Hiwonder-21010732` | With Raspberry Pi 5 (4GB)        |
| `Hiwonder-21010733` | With Raspberry Pi 5 (8GB)        |
| `Hiwonder-21010734` | With Raspberry Pi 5 (16GB)       |
| `Hiwonder-21010797` | Without Jetson Controller        |
| `Hiwonder-21010735` | With Jetson Nano(4GB)            |
| `Hiwonder-21010736` | With Jetson Orin Nano Super(4GB) |
| `Hiwonder-21010737` | With Jetson Orin Nano Super(8GB) |
| `Hiwonder-21010738` | With Jetson Orin NX Super(8GB)   |
| `Hiwonder-21010739` | With Jetson Orin NX Super(16GB)  |

A separately named bracket, horn, chassis or rail is the listed accessory, not a complete robot or servo. A “without controller / Raspberry Pi / Jetson / micro:bit” option requires the matching controller separately. Check the selected option’s packing list before starting.

## Applications

Use NexArm ROS to learn manual motion, perception and staged automation. Start with an unloaded mechanism and the sensors actually included in the selected kit.

## Specifications

| Parameter    | Value / scope                                    |
| ------------ | ------------------------------------------------ |
| Manipulator  | 6-axis NexArm family; configuration as purchased |
| Arm power    | Supplied 12 V adapter; keep host supply separate |
| Host         | Raspberry Pi or Jetson option as named           |
| Camera / kit | Selected vision and kit configuration only       |
| Development  | ROS image and calibration specific to the host   |

Specifications: [manufacturer product data](https://www.hiwonder.com/products/nexarm-ros) and [OpenELAB listing](https://openelab.io/products/hiwonder-nexarm-ros-robotic-arm). Figures describe the stated configuration; accessory-only options do not inherit the complete kit specifications.

## Hardware and connections

Connect the supplied battery or adapter to the **robot’s designated power/expansion board**, not directly to a computer GPIO or an unverified charging socket. Inspect the camera, motor/servo and controller cables while power is off. Secure the base to the work surface and clear the entire arm/gripper envelope. Remove objects from the gripper before startup.

Match the controller, camera, LiDAR and chassis configuration to the SKU. Optional voice/AI modules require their own cables and software. A USB camera, depth camera and CSI ribbon camera are not interchangeable interfaces.

## Software and development resources

Start with the factory image for **NexArm ROS and the exact controller option**. WonderROS is the documented initial control application. Use the official model downloads for restoration; a generic Raspberry Pi OS or JetPack installation does not include the robot services, calibrated offsets and device configuration.

For development, preserve a backup of the supplied image and calibration files before replacing software. Select the manual branch for the installed board and ROS generation. A menu or directory for a different product is not a compatible firmware target. The ROS Appendix may require an order number for image downloads; follow that access route rather than substituting an ESP32 package.

## Getting started

**Prerequisites:** the selected hardware, its matching power source, the required data cable, and a clear work area. Begin with the supplied firmware and an unloaded mechanism.

1. Match the SKU table to the physical controller and kit. For a controller-excluded option, install the supported board and its exact robot image before attempting the remaining steps.
2. Secure the base to the work surface and clear the entire arm/gripper envelope. Remove objects from the gripper before startup. Inspect polarity and cable seating, then power the robot with the supplied matching power system.
3. Allow the onboard computer to finish booting and reach its documented ready posture/indicator state. Keep the mechanism clear because initialization may move servos.
4. Install **WonderROS** from the model’s official resources. Enable Wi-Fi and the local-network/location permissions required for discovery. Select **NexArm**, then **+ → Direct Connection Mode**.
5. Join the robot’s **HW…** hotspot using **hiwonder** on an unchanged factory image. Stay connected if the phone reports no Internet; return to the app and refresh until the correct robot icon appears.
6. Open the model’s Robot/Remote Control screen. Confirm the camera feed, then use a small gripper or single-joint change with no payload. Return to the initial posture and stop; do not begin with an automatic pick sequence.
7. End the demonstration and shut down the onboard operating system before removing power. Keep the original image and configuration until basic control is repeatable.

**Expected result:** The correct robot is discovered, its live camera/connection status is visible, and one small manual command responds and stops predictably. Autonomous tasks and loaded motion remain subsequent tests.

Procedure reference: [official model or interface manual](https://wiki.hiwonder.com/projects/NexArm/en/ros-version/docs/1.%20NexArm%20User%20Manual.html). The steps above are a bounded initial check, not a substitute for the full assembly and development chapters.

## Troubleshooting and FAQs

**No hotspot:** wait for the full boot sequence, verify the battery/adapter and image/controller match, then check whether the robot was previously configured for LAN mode.

**Phone joins Wi-Fi but the app sees nothing:** remain on the robot network despite the no-Internet warning, grant local-network discovery permissions, select the correct model and refresh. The factory password may have been changed on a used unit.

**Camera works but motion is wrong:** stop immediately and verify the chassis type, motor/servo connections and model configuration. Do not compensate with unrelated servo offsets.

**Vision, mapping or voice option is unavailable:** check the selected kit’s actual camera, LiDAR and AI/voice modules. Offline local control does not establish that a cloud AI service is configured.

**Restoring firmware:** use the exact model/controller resource package and retain calibration files; do not write an image for a similarly named Pro or legacy version.

## Downloads and technical documents

* [Official user / interface manual](https://wiki.hiwonder.com/projects/NexArm/en/ros-version/docs/1.%20NexArm%20User%20Manual.html)
* [Official software, image and course downloads](https://wiki.hiwonder.com/projects/NexArm/en/esp32-version/docs/Appendix.html)
* [ROS-version Appendix and download access](https://wiki.hiwonder.com/projects/NexArm/en/ros-version/docs/Appendix.html)
* [Manufacturer Hiwonder NexArm ROS VLA AI Robotic Arm Kit with Jetson/Raspberry Pi Options specifications and option drawings](https://www.hiwonder.com/products/nexarm-ros)

Use the manual’s download or appendix section for the matching revision. A linked download directory is not a claim that every firmware archive, CAD file or installer has been tested. Do not flash an image for a similarly named product.

## References and validation

* [OpenELAB product and SKU options](https://openelab.io/products/hiwonder-nexarm-ros-robotic-arm).
* [Official user / interface manual](https://wiki.hiwonder.com/projects/NexArm/en/ros-version/docs/1.%20NexArm%20User%20Manual.html)
* [Official software, image and course downloads](https://wiki.hiwonder.com/projects/NexArm/en/esp32-version/docs/Appendix.html)
* [ROS-version Appendix and download access](https://wiki.hiwonder.com/projects/NexArm/en/ros-version/docs/Appendix.html)
* [Manufacturer Hiwonder NexArm ROS VLA AI Robotic Arm Kit with Jetson/Raspberry Pi Options specifications and option drawings](https://www.hiwonder.com/products/nexarm-ros)

Reviewed against the linked sources on 19 November 2026. Software installation, compilation and physical hardware tests were not performed for this guide. Use the observable checkpoints above to verify your own unit before integrating it into a larger system.
