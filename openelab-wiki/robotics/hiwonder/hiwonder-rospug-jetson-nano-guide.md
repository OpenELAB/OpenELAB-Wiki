---
description: >-
  ROSPug is a 12-DOF quadruped for gait, balance and vision development. This
  store listing is the Jetson Nano generation; advanced sensors depend on the
  selected kit.
---

# Hiwonder ROSPug Jetson Nano Guide

{% hint style="info" %}
[**View Hiwonder ROSPug Jetson Nano 12DOF ROS Quadruped Robot Dog on OpenELAB**](https://openelab.io/products/hiwonder-rospug-jetson-nano-robot-dog)

**SKU:** `Hiwonder-21040064`

**Model / revision scope:** ROSPug Jetson Nano. Match the purchased option below; hardware revisions and controller images are not interchangeable.
{% endhint %}

![ROSPug Jetson Nano — product image supplied by OpenELAB](../../.gitbook/assets/hiwonder-6.jpg)

## Product overview

ROSPug is a 12-DOF quadruped for gait, balance and vision development. This store listing is the Jetson Nano generation; advanced sensors depend on the selected kit.

### Models and purchasing options

| OpenELAB SKU        | Purchased option |
| ------------------- | ---------------- |
| `Hiwonder-21040064` | Default Title    |

## Applications

Use ROSPug Jetson Nano to learn joint coordination, gait/pose control and camera-based interaction.

## Specifications

| Parameter     | Value / scope                              |
| ------------- | ------------------------------------------ |
| Controller    | Jetson Nano                                |
| Leg actuation | 12 DOF                                     |
| Battery       | 11.1 V, 3500 mAh, 5C as listed             |
| Mass          | Approximately 1.65 kg                      |
| Development   | ROS and Python on the model-specific image |

Specifications: [manufacturer product data](https://www.hiwonder.com/products/rospug) and [OpenELAB listing](https://openelab.io/products/hiwonder-rospug-jetson-nano-robot-dog). Figures describe the stated configuration; accessory-only options do not inherit the complete kit specifications.

## Hardware and connections

Connect the supplied battery or adapter to the **robot’s designated power/expansion board**, not directly to a computer GPIO or an unverified charging socket. Inspect the camera, motor/servo and controller cables while power is off. Keep a clear area around every leg and support the robot in the initial resting posture shown in its model manual. Do not hold a powered joint by hand.

Match the controller, camera, LiDAR and chassis configuration to the SKU. Optional voice/AI modules require their own cables and software. A USB camera, depth camera and CSI ribbon camera are not interchangeable interfaces.

## Software and development resources

Start with the factory image for **ROSPug Jetson Nano and the exact controller option**. WonderROS is the documented initial control application. Use the official model downloads for restoration; a generic Raspberry Pi OS or JetPack installation does not include the robot services, calibrated offsets and device configuration.

For development, preserve a backup of the supplied image and calibration files before replacing software. Select the manual branch for the installed board and ROS generation. A menu or directory for a different product is not a compatible firmware target.

## Getting started

**Prerequisites:** the selected hardware, its matching power source, the required data cable, and a clear work area. Begin with the supplied firmware and an unloaded mechanism.

1. Match the SKU table to the physical controller and kit. For a controller-excluded option, install the supported board and its exact robot image before attempting the remaining steps.
2. Keep a clear area around every leg and support the robot in the initial resting posture shown in its model manual. Do not hold a powered joint by hand. Inspect polarity and cable seating, then power the robot with the supplied matching power system.
3. Allow the onboard computer to finish booting and reach its documented ready posture/indicator state. Keep the mechanism clear because initialization may move servos.
4. Install **WonderROS** from the model’s official resources. Enable Wi-Fi and the local-network/location permissions required for discovery. Select **ROSPug**, then **+ → Direct Connection Mode**.
5. Join the robot’s **HW…** hotspot using **hiwonder** on an unchanged factory image. Stay connected if the phone reports no Internet; return to the app and refresh until the correct robot icon appears.
6. Open the model’s Robot/Remote Control screen and verify the camera feed before issuing a brief low-speed command on a clear floor. Release the control and verify the robot stops; avoid autonomous gaits for this first test.
7. End the demonstration and shut down the onboard operating system before removing power. Keep the original image and configuration until basic control is repeatable.

**Expected result:** The correct robot is discovered, its live camera/connection status is visible, and one small manual command responds and stops predictably. Autonomous tasks and loaded motion remain subsequent tests.

Procedure reference: [official model or interface manual](https://wiki.hiwonder.com/projects/ROSPug/en/latest/docs/2.Quick_User_Exprience.html). The steps above are a bounded initial check, not a substitute for the full assembly and development chapters.

## Troubleshooting and FAQs

**No hotspot:** wait for the full boot sequence, verify the battery/adapter and image/controller match, then check whether the robot was previously configured for LAN mode.

**Phone joins Wi-Fi but the app sees nothing:** remain on the robot network despite the no-Internet warning, grant local-network discovery permissions, select the correct model and refresh. The factory password may have been changed on a used unit.

**Camera works but motion is wrong:** stop immediately and verify the chassis type, motor/servo connections and model configuration. Do not compensate with unrelated servo offsets.

**Vision, mapping or voice option is unavailable:** check the selected kit’s actual camera, LiDAR and AI/voice modules. Offline local control does not establish that a cloud AI service is configured.

**Restoring firmware:** use the exact model/controller resource package and retain calibration files; do not write an image for a similarly named Pro or legacy version.

## Downloads and technical documents

* [Official user / interface manual](https://wiki.hiwonder.com/projects/ROSPug/en/latest/docs/2.Quick_User_Exprience.html)
* [Official software, image and course downloads](https://wiki.hiwonder.com/projects/ROSPug/en/latest/docs/Appendix.html)
* [Manufacturer Hiwonder ROSPug Jetson Nano 12DOF ROS Quadruped Robot Dog specifications and option drawings](https://www.hiwonder.com/products/rospug)

Use the manual’s download or appendix section for the matching revision. A linked download directory is not a claim that every firmware archive, CAD file or installer has been tested. Do not flash an image for a similarly named product.

## References and validation

* [OpenELAB product and SKU options](https://openelab.io/products/hiwonder-rospug-jetson-nano-robot-dog).
* [Official user / interface manual](https://wiki.hiwonder.com/projects/ROSPug/en/latest/docs/2.Quick_User_Exprience.html)
* [Official software, image and course downloads](https://wiki.hiwonder.com/projects/ROSPug/en/latest/docs/Appendix.html)
* [Manufacturer Hiwonder ROSPug Jetson Nano 12DOF ROS Quadruped Robot Dog specifications and option drawings](https://www.hiwonder.com/products/rospug)

Reviewed against the linked sources on 19 November 2026. Software installation, compilation and physical hardware tests were not performed for this guide. Use the observable checkpoints above to verify your own unit before integrating it into a larger system.
