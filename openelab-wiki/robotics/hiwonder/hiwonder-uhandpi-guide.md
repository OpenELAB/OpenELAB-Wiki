---
description: >-
  A camera-equipped Raspberry Pi robotic hand with five finger actuators and a
  pan axis.
---

# Hiwonder uHandPi Guide

{% hint style="info" %}
[**View Hiwonder uHandPi 6DOF AI Vision Robotic Hand Kit with Raspberry Pi 5 on OpenELAB**](https://openelab.io/products/uhandpi-pi5)

**SKU:** `Hiwonder-21050042`, `Hiwonder-21050043`, `Hiwonder-21050025`, `Hiwonder-21050021`, `Hiwonder-21050026`, `Hiwonder-21050022`

**Model / revision scope:** uHandPi. Match the purchased option below; hardware revisions and controller images are not interchangeable.
{% endhint %}

![uHandPi — product image supplied by OpenELAB](../../.gitbook/assets/hiwonder-101.jpg)

## Product overview

A camera-equipped Raspberry Pi robotic hand with five finger actuators and a pan axis.

Some shared app-connection paragraphs retain a TurboPi label. Use the uHandPi model entry and its own control screen; the linked manual’s model-specific feature section identifies that screen.

### Models and purchasing options

| OpenELAB SKU        | Purchased option                       |
| ------------------- | -------------------------------------- |
| `Hiwonder-21050042` | With Raspberry Pi 5 (2GB) / Left hand  |
| `Hiwonder-21050043` | With Raspberry Pi 5 (2GB) / Right hand |
| `Hiwonder-21050025` | With Raspberry Pi 5 (4GB) / Left hand  |
| `Hiwonder-21050021` | With Raspberry Pi 5 (4GB) / Right hand |
| `Hiwonder-21050026` | With Raspberry Pi 5 (8GB) / Left hand  |
| `Hiwonder-21050022` | With Raspberry Pi 5 (8GB) / Right hand |

## Applications

Use uHandPi to learn manual motion, perception and staged automation. Start with an unloaded mechanism and the sensors actually included in the selected kit.

## Specifications

| Parameter      | Value / scope                                      |
| -------------- | -------------------------------------------------- |
| Controller     | Raspberry Pi, exact included/excluded option below |
| Power          | 7.5 V, 6 A supplied adapter                        |
| Mechanism      | 6 DOF total                                        |
| Mass reference | Approximately 0.56 kg                              |

Specifications: [manufacturer product data](https://www.hiwonder.com/products/uhandpi) and [OpenELAB listing](https://openelab.io/products/uhandpi-pi5). Figures describe the stated configuration; accessory-only options do not inherit the complete kit specifications.

## Hardware and connections

Connect the supplied battery or adapter to the **robot’s designated power/expansion board**, not directly to a computer GPIO or an unverified charging socket. Inspect the camera, motor/servo and controller cables while power is off. Secure the hand base and keep the fingers and pan axis clear. Leave the gripper/fingers unloaded.

Match the controller, camera, LiDAR and chassis configuration to the SKU. Optional voice/AI modules require their own cables and software. A USB camera, depth camera and CSI ribbon camera are not interchangeable interfaces.

## Software and development resources

Start with the factory image for **uHandPi and the exact controller option**. WonderPi is the documented initial control application. Use the official model downloads for restoration; a generic Raspberry Pi OS or JetPack installation does not include the robot services, calibrated offsets and device configuration.

For development, preserve a backup of the supplied image and calibration files before replacing software. Select the manual branch for the installed board and ROS generation. A menu or directory for a different product is not a compatible firmware target.

## Getting started

**Prerequisites:** the selected hardware, its matching power source, the required data cable, and a clear work area. Begin with the supplied firmware and an unloaded mechanism.

1. Match the SKU table to the physical controller and kit. For a controller-excluded option, install the supported board and its exact robot image before attempting the remaining steps.
2. Secure the hand base and keep the fingers and pan axis clear. Leave the gripper/fingers unloaded. Inspect polarity and cable seating, then power the robot with the supplied matching power system.
3. Allow the onboard computer to finish booting and reach its documented ready posture/indicator state. Keep the mechanism clear because initialization may move servos.
4. Install **WonderPi** from the model’s official resources. Enable Wi-Fi and the local-network/location permissions required for discovery. Select **uHandPi**, then **+ → Direct Connection Mode**.
5. Join the robot’s **HW…** hotspot using **hiwonder** on an unchanged factory image. Stay connected if the phone reports no Internet; return to the app and refresh until the correct robot icon appears.
6. Open Remote Control, verify the camera image, and make one small finger command. Return to the starting position; keep hands clear of the mechanism.
7. End the demonstration and shut down the onboard operating system before removing power. Keep the original image and configuration until basic control is repeatable.

**Expected result:** The correct robot is discovered, its live camera/connection status is visible, and one small manual command responds and stops predictably. Autonomous tasks and loaded motion remain subsequent tests.

Procedure reference: [official model or interface manual](https://wiki.hiwonder.com/projects/uHandPi/en/latest/docs/2.quick_user_experience.html). The steps above are a bounded initial check, not a substitute for the full assembly and development chapters.

## Troubleshooting and FAQs

**No hotspot:** wait for the full boot sequence, verify the battery/adapter and image/controller match, then check whether the robot was previously configured for LAN mode.

**Phone joins Wi-Fi but the app sees nothing:** remain on the robot network despite the no-Internet warning, grant local-network discovery permissions, select the correct model and refresh. The factory password may have been changed on a used unit.

**Camera works but motion is wrong:** stop immediately and verify the chassis type, motor/servo connections and model configuration. Do not compensate with unrelated servo offsets.

**Vision, mapping or voice option is unavailable:** check the selected kit’s actual camera, LiDAR and AI/voice modules. Offline local control does not establish that a cloud AI service is configured.

**Restoring firmware:** use the exact model/controller resource package and retain calibration files; do not write an image for a similarly named Pro or legacy version.

## Downloads and technical documents

* [Official user / interface manual](https://wiki.hiwonder.com/projects/uHandPi/en/latest/docs/2.quick_user_experience.html)
* [Official software, image and course downloads](https://wiki.hiwonder.com/projects/uHandPi/en/latest/docs/resources_download.html)
* [Model assembly, power and startup manual](https://wiki.hiwonder.com/projects/uHandPi/en/latest/docs/1.getting_ready.html)
* [Manufacturer Hiwonder uHandPi 6DOF AI Vision Robotic Hand Kit with Raspberry Pi 5 specifications and option drawings](https://www.hiwonder.com/products/uhandpi)

Use the manual’s download or appendix section for the matching revision. A linked download directory is not a claim that every firmware archive, CAD file or installer has been tested. Do not flash an image for a similarly named product.

## References and validation

* [OpenELAB product and SKU options](https://openelab.io/products/uhandpi-pi5).
* [Official user / interface manual](https://wiki.hiwonder.com/projects/uHandPi/en/latest/docs/2.quick_user_experience.html)
* [Official software, image and course downloads](https://wiki.hiwonder.com/projects/uHandPi/en/latest/docs/resources_download.html)
* [Model assembly, power and startup manual](https://wiki.hiwonder.com/projects/uHandPi/en/latest/docs/1.getting_ready.html)
* [Manufacturer Hiwonder uHandPi 6DOF AI Vision Robotic Hand Kit with Raspberry Pi 5 specifications and option drawings](https://www.hiwonder.com/products/uhandpi)

Reviewed against the linked sources on 19 November 2026. Software installation, compilation and physical hardware tests were not performed for this guide. Use the observable checkpoints above to verify your own unit before integrating it into a larger system.
