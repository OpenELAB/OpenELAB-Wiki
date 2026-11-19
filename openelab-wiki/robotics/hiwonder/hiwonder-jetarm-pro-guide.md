---
description: >-
  JetArm Pro is the enhanced desktop vision-arm configuration in the JetArm
  family. The manufacturer links both models to the JetArm documentation; use
  its controller branch and the kit-specific arm/cam
---

# Hiwonder JetArm Pro Guide

{% hint style="info" %}
[**View Hiwonder JetArm Pro ROS1/ROS2 3D Vision AI Robot Arm Kit for Jetson on OpenELAB**](https://openelab.io/products/jetarm-pro-ros2)

**SKU:** `Hiwonder-21030674`, `Hiwonder-21030675`, `Hiwonder-21030677`, `Hiwonder-21030676`, `Hiwonder-21030678`, `Hiwonder-21030679`, `Hiwonder-21030681`, `Hiwonder-21030680`, `Hiwonder-21030682`, `Hiwonder-21030683`, `Hiwonder-21030685`, `Hiwonder-21030684`, `Hiwonder-21030686`, `Hiwonder-21030687`, `Hiwonder-21030689`, `Hiwonder-21030688`, `Hiwonder-21030690`, `Hiwonder-21030691`, `Hiwonder-21030693`, `Hiwonder-21030692`, `Hiwonder-21030694`, `Hiwonder-21030695`, `Hiwonder-21030697`, `Hiwonder-21030696`, `Hiwonder-21030710`, `Hiwonder-21030711`, `Hiwonder-21030713`, `Hiwonder-21030712`, `Hiwonder-21030714`, `Hiwonder-21030715`, `Hiwonder-21030717`, `Hiwonder-21030716`, `Hiwonder-21030718`, `Hiwonder-21030719`, `Hiwonder-21030721`, `Hiwonder-21030720`

**Model / revision scope:** JetArm Pro. Match the purchased option below; hardware revisions and controller images are not interchangeable.
{% endhint %}

![JetArm Pro — product image supplied by OpenELAB](../../.gitbook/assets/hiwonder-94.png)

## Product overview

JetArm Pro is the enhanced desktop vision-arm configuration in the JetArm family. The manufacturer links both models to the JetArm documentation; use its controller branch and the kit-specific arm/camera configuration.

**Power separation:** where a host adapter and arm adapter are both supplied, follow their labelled connections. The 19 V host adapter must not be inserted into the 12 V servo/arm power input. Confirm the selected controller’s diagram before power-on. The shared app chapter uses the JetArm entry; it does not document a separate JetArm Pro entry. Confirm the actual arm configuration before motion.

### Models and purchasing options

| OpenELAB SKU        | Purchased option                                                  |
| ------------------- | ----------------------------------------------------------------- |
| `Hiwonder-21030674` | Standard Kit / With Jetson Nano(4GB) / Mecanum Chassis            |
| `Hiwonder-21030675` | Standard Kit / With Jetson Nano(4GB) / Tank Chassis               |
| `Hiwonder-21030677` | Standard Kit / With Jetson Nano(4GB) / Conveyor Belt              |
| `Hiwonder-21030676` | Standard Kit / With Jetson Nano(4GB) / Sliding Rail               |
| `Hiwonder-21030678` | Standard Kit / With Jetson Orin Nano Super(8GB) / Mecanum Chassis |
| `Hiwonder-21030679` | Standard Kit / With Jetson Orin Nano Super(8GB) / Tank Chassis    |
| `Hiwonder-21030681` | Standard Kit / With Jetson Orin Nano Super(8GB) / Conveyor Belt   |
| `Hiwonder-21030680` | Standard Kit / With Jetson Orin Nano Super(8GB) / Sliding Rail    |
| `Hiwonder-21030682` | Standard Kit / With Jetson Orin NX Super(16GB) / Mecanum Chassis  |
| `Hiwonder-21030683` | Standard Kit / With Jetson Orin NX Super(16GB) / Tank Chassis     |
| `Hiwonder-21030685` | Standard Kit / With Jetson Orin NX Super(16GB) / Conveyor Belt    |
| `Hiwonder-21030684` | Standard Kit / With Jetson Orin NX Super(16GB) / Sliding Rail     |
| `Hiwonder-21030686` | Advanced Kit / With Jetson Nano(4GB) / Mecanum Chassis            |
| `Hiwonder-21030687` | Advanced Kit / With Jetson Nano(4GB) / Tank Chassis               |
| `Hiwonder-21030689` | Advanced Kit / With Jetson Nano(4GB) / Conveyor Belt              |
| `Hiwonder-21030688` | Advanced Kit / With Jetson Nano(4GB) / Sliding Rail               |
| `Hiwonder-21030690` | Advanced Kit / With Jetson Orin Nano Super(8GB) / Mecanum Chassis |
| `Hiwonder-21030691` | Advanced Kit / With Jetson Orin Nano Super(8GB) / Tank Chassis    |
| `Hiwonder-21030693` | Advanced Kit / With Jetson Orin Nano Super(8GB) / Conveyor Belt   |
| `Hiwonder-21030692` | Advanced Kit / With Jetson Orin Nano Super(8GB) / Sliding Rail    |
| `Hiwonder-21030694` | Advanced Kit / With Jetson Orin NX Super(16GB) / Mecanum Chassis  |
| `Hiwonder-21030695` | Advanced Kit / With Jetson Orin NX Super(16GB) / Tank Chassis     |
| `Hiwonder-21030697` | Advanced Kit / With Jetson Orin NX Super(16GB) / Conveyor Belt    |
| `Hiwonder-21030696` | Advanced Kit / With Jetson Orin NX Super(16GB) / Sliding Rail     |
| `Hiwonder-21030710` | Ultimate Kit / With Jetson Nano(4GB) / Mecanum Chassis            |
| `Hiwonder-21030711` | Ultimate Kit / With Jetson Nano(4GB) / Tank Chassis               |
| `Hiwonder-21030713` | Ultimate Kit / With Jetson Nano(4GB) / Conveyor Belt              |
| `Hiwonder-21030712` | Ultimate Kit / With Jetson Nano(4GB) / Sliding Rail               |
| `Hiwonder-21030714` | Ultimate Kit / With Jetson Orin Nano Super(8GB) / Mecanum Chassis |
| `Hiwonder-21030715` | Ultimate Kit / With Jetson Orin Nano Super(8GB) / Tank Chassis    |
| `Hiwonder-21030717` | Ultimate Kit / With Jetson Orin Nano Super(8GB) / Conveyor Belt   |
| `Hiwonder-21030716` | Ultimate Kit / With Jetson Orin Nano Super(8GB) / Sliding Rail    |
| `Hiwonder-21030718` | Ultimate Kit / With Jetson Orin NX Super(16GB) / Mecanum Chassis  |
| `Hiwonder-21030719` | Ultimate Kit / With Jetson Orin NX Super(16GB) / Tank Chassis     |
| `Hiwonder-21030721` | Ultimate Kit / With Jetson Orin NX Super(16GB) / Conveyor Belt    |
| `Hiwonder-21030720` | Ultimate Kit / With Jetson Orin NX Super(16GB) / Sliding Rail     |

A separately named bracket, horn, chassis or rail is the listed accessory, not a complete robot or servo. A “without controller / Raspberry Pi / Jetson / micro:bit” option requires the matching controller separately. Check the selected option’s packing list before starting.

## Applications

Use JetArm Pro to learn manual motion, perception and staged automation. Start with an unloaded mechanism and the sensors actually included in the selected kit.

## Specifications

| Parameter               | Value / scope                                                                 |
| ----------------------- | ----------------------------------------------------------------------------- |
| Controller              | Jetson / Raspberry Pi variants as selected                                    |
| Arm supply              | 12 V, 5 A in the arm manual                                                   |
| Additional host adapter | 19 V, 2.37 A listed for applicable host configurations; separate power domain |
| Camera                  | Depth-camera option varies by kit                                             |
| System                  | Model-specific ROS image and calibration                                      |

Specifications: [manufacturer product data](https://www.hiwonder.com/products/jetarm-pro) and [OpenELAB listing](https://openelab.io/products/jetarm-pro-ros2). Figures describe the stated configuration; accessory-only options do not inherit the complete kit specifications.

## Hardware and connections

Connect the supplied battery or adapter to the **robot’s designated power/expansion board**, not directly to a computer GPIO or an unverified charging socket. Inspect the camera, motor/servo and controller cables while power is off. Secure the base to the work surface and clear the entire arm/gripper envelope. Remove objects from the gripper before startup.

Match the controller, camera, LiDAR and chassis configuration to the SKU. Optional voice/AI modules require their own cables and software. A USB camera, depth camera and CSI ribbon camera are not interchangeable interfaces.

## Software and development resources

Start with the factory image for **JetArm Pro and the exact controller option**. WonderAi is the documented initial control application. Use the official model downloads for restoration; a generic Raspberry Pi OS or JetPack installation does not include the robot services, calibrated offsets and device configuration.

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
* [Manufacturer Hiwonder JetArm Pro ROS1/ROS2 3D Vision AI Robot Arm Kit for Jetson specifications and option drawings](https://www.hiwonder.com/products/jetarm-pro)

Use the manual’s download or appendix section for the matching revision. A linked download directory is not a claim that every firmware archive, CAD file or installer has been tested. Do not flash an image for a similarly named product.

## References and validation

* [OpenELAB product and SKU options](https://openelab.io/products/jetarm-pro-ros2).
* [Official user / interface manual](https://wiki.hiwonder.com/projects/JetArm/en/jetarm-orin-nano/docs/1.Getting_Ready.html)
* [Official software, image and course downloads](https://wiki.hiwonder.com/projects/JetArm/en/jetarm-orin-nano/docs/resources_download.html)
* [Manufacturer Hiwonder JetArm Pro ROS1/ROS2 3D Vision AI Robot Arm Kit for Jetson specifications and option drawings](https://www.hiwonder.com/products/jetarm-pro)

Reviewed against the linked sources on 19 November 2026. Software installation, compilation and physical hardware tests were not performed for this guide. Use the observable checkpoints above to verify your own unit before integrating it into a larger system.
