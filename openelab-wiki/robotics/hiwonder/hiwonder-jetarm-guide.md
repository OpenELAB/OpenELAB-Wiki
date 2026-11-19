---
description: >-
  JetArm is a desktop vision arm for ROS, perception and manipulation exercises.
  Choose the correct host and depth-camera version before installing software.
---

# Hiwonder JetArm Guide

{% hint style="info" %}
[**View Hiwonder JetArm ROS Robot Arm with Jetson, 3D Vision, AI Grasping & Voice on OpenELAB**](https://openelab.io/products/jetarm-ai-robot-arm)

**SKU:** `Hiwonder-21010192`, `Hiwonder-21010193`, `Hiwonder-21010212`, `Hiwonder-21010213`, `Hiwonder-21010214`, `Hiwonder-21010215`, `Hiwonder-21010217`, `Hiwonder-21010196`, `Hiwonder-21010189`, `Hiwonder-21010216`, `Hiwonder-21010218`, `Hiwonder-21010219`, `Hiwonder-21010222`, `Hiwonder-21010198`, `Hiwonder-21010197`, `Hiwonder-21010201`, `Hiwonder-21010220`, `Hiwonder-21010221`, `Hiwonder-21010227`, `Hiwonder-21010226`, `Hiwonder-21010188`, `Hiwonder-21010223`, `Hiwonder-21010224`, `Hiwonder-21010225`

**Model / revision scope:** JetArm. Match the purchased option below; hardware revisions and controller images are not interchangeable.
{% endhint %}

![JetArm — product image supplied by OpenELAB](../../.gitbook/assets/hiwonder-85.png)

## Product overview

JetArm is a desktop vision arm for ROS, perception and manipulation exercises. Choose the correct host and depth-camera version before installing software.

**Power separation:** where a host adapter and arm adapter are both supplied, follow their labelled connections. The 19 V host adapter must not be inserted into the 12 V servo/arm power input. Confirm the selected controller’s diagram before power-on.

### Models and purchasing options

| OpenELAB SKU        | Purchased option                                |
| ------------------- | ----------------------------------------------- |
| `Hiwonder-21010192` | Starter Kit / Without Jetson Controller         |
| `Hiwonder-21010193` | Starter Kit / With Jetson Nano(4GB)             |
| `Hiwonder-21010212` | Starter Kit / With Jetson Orin Nano Super(4GB)  |
| `Hiwonder-21010213` | Starter Kit / With Jetson Orin Nano Super(8GB)  |
| `Hiwonder-21010214` | Starter Kit / With Jetson Orin NX Super(8GB)    |
| `Hiwonder-21010215` | Starter Kit / With Jetson Orin NX Super(16GB)   |
| `Hiwonder-21010217` | Standard Kit / Without Jetson Controller        |
| `Hiwonder-21010196` | Standard Kit / With Jetson Nano(4GB)            |
| `Hiwonder-21010189` | Standard Kit / With Jetson Orin Nano Super(4GB) |
| `Hiwonder-21010216` | Standard Kit / With Jetson Orin Nano Super(8GB) |
| `Hiwonder-21010218` | Standard Kit / With Jetson Orin NX Super(8GB)   |
| `Hiwonder-21010219` | Standard Kit / With Jetson Orin NX Super(16GB)  |
| `Hiwonder-21010222` | Advanced Kit / Without Jetson Controller        |
| `Hiwonder-21010198` | Advanced Kit / With Jetson Nano(4GB)            |
| `Hiwonder-21010197` | Advanced Kit / With Jetson Orin Nano Super(4GB) |
| `Hiwonder-21010201` | Advanced Kit / With Jetson Orin Nano Super(8GB) |
| `Hiwonder-21010220` | Advanced Kit / With Jetson Orin NX Super(8GB)   |
| `Hiwonder-21010221` | Advanced Kit / With Jetson Orin NX Super(16GB)  |
| `Hiwonder-21010227` | Ultimate Kit / Without Jetson Controller        |
| `Hiwonder-21010226` | Ultimate Kit / With Jetson Nano(4GB)            |
| `Hiwonder-21010188` | Ultimate Kit / With Jetson Orin Nano Super(4GB) |
| `Hiwonder-21010223` | Ultimate Kit / With Jetson Orin Nano Super(8GB) |
| `Hiwonder-21010224` | Ultimate Kit / With Jetson Orin NX Super(8GB)   |
| `Hiwonder-21010225` | Ultimate Kit / With Jetson Orin NX Super(16GB)  |

A separately named bracket, horn, chassis or rail is the listed accessory, not a complete robot or servo. A “without controller / Raspberry Pi / Jetson / micro:bit” option requires the matching controller separately. Check the selected option’s packing list before starting.

## Applications

Use JetArm to learn manual motion, perception and staged automation. Start with an unloaded mechanism and the sensors actually included in the selected kit.

## Specifications

| Parameter               | Value / scope                                                                 |
| ----------------------- | ----------------------------------------------------------------------------- |
| Controller              | Jetson / Raspberry Pi variants as selected                                    |
| Arm supply              | 12 V, 5 A in the arm manual                                                   |
| Additional host adapter | 19 V, 2.37 A listed for applicable host configurations; separate power domain |
| Camera                  | Depth-camera option varies by kit                                             |
| System                  | Model-specific ROS image and calibration                                      |

Specifications: [manufacturer product data](https://www.hiwonder.com/products/jetarm) and [OpenELAB listing](https://openelab.io/products/jetarm-ai-robot-arm). Figures describe the stated configuration; accessory-only options do not inherit the complete kit specifications.

## Hardware and connections

Connect the supplied battery or adapter to the **robot’s designated power/expansion board**, not directly to a computer GPIO or an unverified charging socket. Inspect the camera, motor/servo and controller cables while power is off. Secure the base to the work surface and clear the entire arm/gripper envelope. Remove objects from the gripper before startup.

Match the controller, camera, LiDAR and chassis configuration to the SKU. Optional voice/AI modules require their own cables and software. A USB camera, depth camera and CSI ribbon camera are not interchangeable interfaces.

## Software and development resources

Start with the factory image for **JetArm and the exact controller option**. WonderAi is the documented initial control application. Use the official model downloads for restoration; a generic Raspberry Pi OS or JetPack installation does not include the robot services, calibrated offsets and device configuration.

For development, preserve a backup of the supplied image and calibration files before replacing software. Select the manual branch for the installed board and ROS generation. A menu or directory for a different product is not a compatible firmware target.

## Getting started

**Prerequisites:** the selected hardware, its matching power source, the required data cable, and a clear work area. Begin with the supplied firmware and an unloaded mechanism.

1. Match the SKU table to the physical controller and kit. For a controller-excluded option, install the supported board and its exact robot image before attempting the remaining steps.
2. Secure the base to the work surface and clear the entire arm/gripper envelope. Remove objects from the gripper before startup. Inspect polarity and cable seating, then power the robot with the supplied matching power system.
3. Allow the onboard computer to finish booting and reach its documented ready posture/indicator state. Keep the mechanism clear because initialization may move servos.
4. Install **WonderAi** from the model’s official resources. Enable Wi-Fi and the local-network/location permissions required for discovery. Select **Advanced → JetArm**, then **+ → Direct Connection Mode**.
5. Join the robot’s **HW…** hotspot using **hiwonder** on an unchanged factory image. Stay connected if the phone reports no Internet; return to the app and refresh until the correct robot icon appears.
6. Open the model’s Robot/Remote Control screen. Confirm the camera feed, then use a small gripper or single-joint change with no payload. Return to the initial posture and stop; do not begin with an automatic pick sequence.
7. End the demonstration and shut down the onboard operating system before removing power. Keep the original image and configuration until basic control is repeatable.

**Expected result:** The correct robot is discovered, its live camera/connection status is visible, and one small manual command responds and stops predictably. Autonomous tasks and loaded motion remain subsequent tests.

Procedure reference: [official model or interface manual](https://wiki.hiwonder.com/projects/JetArm/en/jetarm-orin-nano/docs/1.Getting_Ready.html). The steps above are a bounded initial check, not a substitute for the full assembly and development chapters.

## Troubleshooting and FAQs

**No hotspot:** wait for the full boot sequence, verify the battery/adapter and image/controller match, then check whether the robot was previously configured for LAN mode.

**Phone joins Wi-Fi but the app sees nothing:** remain on the robot network despite the no-Internet warning, grant local-network discovery permissions, select the correct model and refresh. The factory password may have been changed on a used unit.

**Camera works but motion is wrong:** stop immediately and verify the chassis type, motor/servo connections and model configuration. Do not compensate with unrelated servo offsets.

**Vision, mapping or voice option is unavailable:** check the selected kit’s actual camera, LiDAR and AI/voice modules. Offline local control does not establish that a cloud AI service is configured.

**Restoring firmware:** use the exact model/controller resource package and retain calibration files; do not write an image for a similarly named Pro or legacy version.

## Downloads and technical documents

* [Official user / interface manual](https://wiki.hiwonder.com/projects/JetArm/en/jetarm-orin-nano/docs/1.Getting_Ready.html)
* [Official software, image and course downloads](https://wiki.hiwonder.com/projects/JetArm/en/jetarm-orin-nano/docs/resources_download.html)
* [Manufacturer Hiwonder JetArm ROS Robot Arm with Jetson, 3D Vision, AI Grasping & Voice specifications and option drawings](https://www.hiwonder.com/products/jetarm)

Use the manual’s download or appendix section for the matching revision. A linked download directory is not a claim that every firmware archive, CAD file or installer has been tested. Do not flash an image for a similarly named product.

## References and validation

* [OpenELAB product and SKU options](https://openelab.io/products/jetarm-ai-robot-arm).
* [Official user / interface manual](https://wiki.hiwonder.com/projects/JetArm/en/jetarm-orin-nano/docs/1.Getting_Ready.html)
* [Official software, image and course downloads](https://wiki.hiwonder.com/projects/JetArm/en/jetarm-orin-nano/docs/resources_download.html)
* [Manufacturer Hiwonder JetArm ROS Robot Arm with Jetson, 3D Vision, AI Grasping & Voice specifications and option drawings](https://www.hiwonder.com/products/jetarm)

Reviewed against the linked sources on 19 November 2026. Software installation, compilation and physical hardware tests were not performed for this guide. Use the observable checkpoints above to verify your own unit before integrating it into a larger system.
