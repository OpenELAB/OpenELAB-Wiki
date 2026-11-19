---
description: A mobile Mecanum-base arm for vision-guided transport and ROS learning.
---

# Hiwonder ArmPi Pro Guide

{% hint style="info" %}
[**View Hiwonder ArmPi Pro ROS AI Vision Robot Arm with Mecanum Chassis on OpenELAB**](https://openelab.io/products/armpi-pro-pi5)

**SKU:** `Hiwonder-21030233`, `Hiwonder-21030023`, `Hiwonder-21031915`, `Hiwonder-21030215`, `Hiwonder-21030214`

**Model / revision scope:** ArmPi Pro. Match the purchased option below; hardware revisions and controller images are not interchangeable.
{% endhint %}

![ArmPi Pro — product image supplied by OpenELAB](../../.gitbook/assets/hiwonder-103.png)

## Product overview

A mobile Mecanum-base arm for vision-guided transport and ROS learning.

Some shared app-connection paragraphs retain a TurboPi label. Use the ArmPi Pro model entry and its own control screen; the linked manual’s model-specific feature section identifies that screen.

### Models and purchasing options

| OpenELAB SKU        | Purchased option      |
| ------------------- | --------------------- |
| `Hiwonder-21030233` | Without Raspberry Pi  |
| `Hiwonder-21030023` | Raspberry Pi 4B (4GB) |
| `Hiwonder-21031915` | Raspberry Pi 5 (2GB)  |
| `Hiwonder-21030215` | Raspberry Pi 5 (4GB)  |
| `Hiwonder-21030214` | Raspberry Pi 5 (8GB)  |

A separately named bracket, horn, chassis or rail is the listed accessory, not a complete robot or servo. A “without controller / Raspberry Pi / Jetson / micro:bit” option requires the matching controller separately. Check the selected option’s packing list before starting.

## Applications

Use ArmPi Pro to learn manual motion, perception and staged automation. Start with an unloaded mechanism and the sensors actually included in the selected kit.

## Specifications

| Parameter      | Value / scope                                       |
| -------------- | --------------------------------------------------- |
| Controller     | Raspberry Pi, exact included/excluded option below  |
| Power          | 7.4 V, 6000 mAh, 3C battery; matching 8.4 V charger |
| Mechanism      | Mobile arm; separate base and arm control           |
| Mass reference | Approximately 3.6 kg                                |

Specifications: [manufacturer product data](https://www.hiwonder.com/products/armpi-pro) and [OpenELAB listing](https://openelab.io/products/armpi-pro-pi5). Figures describe the stated configuration; accessory-only options do not inherit the complete kit specifications.

## Hardware and connections

Connect the supplied battery or adapter to the **robot’s designated power/expansion board**, not directly to a computer GPIO or an unverified charging socket. Inspect the camera, motor/servo and controller cables while power is off. Secure the base to the work surface and clear the entire arm/gripper envelope. Remove objects from the gripper before startup.

Match the controller, camera, LiDAR and chassis configuration to the SKU. Optional voice/AI modules require their own cables and software. A USB camera, depth camera and CSI ribbon camera are not interchangeable interfaces.

## Software and development resources

Start with the factory image for **ArmPi Pro and the exact controller option**. WonderPi is the documented initial control application. Use the official model downloads for restoration; a generic Raspberry Pi OS or JetPack installation does not include the robot services, calibrated offsets and device configuration.

For development, preserve a backup of the supplied image and calibration files before replacing software. Select the manual branch for the installed board and ROS generation. A menu or directory for a different product is not a compatible firmware target.

## Getting started

**Prerequisites:** the selected hardware, its matching power source, the required data cable, and a clear work area. Begin with the supplied firmware and an unloaded mechanism.

1. Match the SKU table to the physical controller and kit. For a controller-excluded option, install the supported board and its exact robot image before attempting the remaining steps.
2. Secure the base to the work surface and clear the entire arm/gripper envelope. Remove objects from the gripper before startup. Inspect polarity and cable seating, then power the robot with the supplied matching power system.
3. Allow the onboard computer to finish booting and reach its documented ready posture/indicator state. Keep the mechanism clear because initialization may move servos.
4. Install **WonderPi** from the model’s official resources. Enable Wi-Fi and the local-network/location permissions required for discovery. Select **ArmPi Pro**, then **+ → Direct Connection Mode**.
5. Join the robot’s **HW…** hotspot using **hiwonder** on an unchanged factory image. Stay connected if the phone reports no Internet; return to the app and refresh until the correct robot icon appears.
6. Open the model’s Robot/Remote Control screen. Confirm the camera feed, then use a small gripper or single-joint change with no payload. Return to the initial posture and stop; do not begin with an automatic pick sequence.
7. End the demonstration and shut down the onboard operating system before removing power. Keep the original image and configuration until basic control is repeatable.

**Expected result:** The correct robot is discovered, its live camera/connection status is visible, and one small manual command responds and stops predictably. Autonomous tasks and loaded motion remain subsequent tests.

Procedure reference: [official model or interface manual](https://wiki.hiwonder.com/projects/ArmPi_Pro/en/latest/docs/2_play_first_hand.html). The steps above are a bounded initial check, not a substitute for the full assembly and development chapters.

## Troubleshooting and FAQs

**No hotspot:** wait for the full boot sequence, verify the battery/adapter and image/controller match, then check whether the robot was previously configured for LAN mode.

**Phone joins Wi-Fi but the app sees nothing:** remain on the robot network despite the no-Internet warning, grant local-network discovery permissions, select the correct model and refresh. The factory password may have been changed on a used unit.

**Camera works but motion is wrong:** stop immediately and verify the chassis type, motor/servo connections and model configuration. Do not compensate with unrelated servo offsets.

**Vision, mapping or voice option is unavailable:** check the selected kit’s actual camera, LiDAR and AI/voice modules. Offline local control does not establish that a cloud AI service is configured.

**Restoring firmware:** use the exact model/controller resource package and retain calibration files; do not write an image for a similarly named Pro or legacy version.

## Downloads and technical documents

* [Official user / interface manual](https://wiki.hiwonder.com/projects/ArmPi_Pro/en/latest/docs/2_play_first_hand.html)
* [Model assembly, power and startup manual](https://wiki.hiwonder.com/projects/ArmPi_Pro/en/latest/docs/1_read_before_studying.html)
* [Manufacturer Hiwonder ArmPi Pro ROS AI Vision Robot Arm with Mecanum Chassis specifications and option drawings](https://www.hiwonder.com/products/armpi-pro)

Use the manual’s download or appendix section for the matching revision. A linked download directory is not a claim that every firmware archive, CAD file or installer has been tested. Do not flash an image for a similarly named product.

## References and validation

* [OpenELAB product and SKU options](https://openelab.io/products/armpi-pro-pi5).
* [Official user / interface manual](https://wiki.hiwonder.com/projects/ArmPi_Pro/en/latest/docs/2_play_first_hand.html)
* [Model assembly, power and startup manual](https://wiki.hiwonder.com/projects/ArmPi_Pro/en/latest/docs/1_read_before_studying.html)
* [Manufacturer Hiwonder ArmPi Pro ROS AI Vision Robot Arm with Mecanum Chassis specifications and option drawings](https://www.hiwonder.com/products/armpi-pro)

Reviewed against the linked sources on 19 November 2026. Software installation, compilation and physical hardware tests were not performed for this guide. Use the observable checkpoints above to verify your own unit before integrating it into a larger system.
