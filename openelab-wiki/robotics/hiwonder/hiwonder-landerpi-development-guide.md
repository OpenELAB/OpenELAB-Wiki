---
description: >-
  LanderPi is a Raspberry Pi ROS2 mobile manipulator offered with Mecanum,
  Ackermann and tracked chassis. Its 45 options must be matched to the correct
  chassis, controller and kit configuration.
---

# Hiwonder LanderPi Guide

{% hint style="info" %}
[**View Hiwonder LanderPi ROS2 Robot Car Kit - 6DOF Arm & LiDAR on OpenELAB**](https://openelab.io/products/landerpi-robot-car)

**SKU:** `Hiwonder-21031613`, `Hiwonder-21031625`, `Hiwonder-21031637`, `Hiwonder-21031916`, `Hiwonder-21031919`, `Hiwonder-21031922`, `Hiwonder-21031614`, `Hiwonder-21031626`, `Hiwonder-21031638`, `Hiwonder-21031615`, `Hiwonder-21031627`, `Hiwonder-21031639`, `Hiwonder-21031616`, `Hiwonder-21031628`, `Hiwonder-21031640`, `Hiwonder-21031617`, `Hiwonder-21031629`, `Hiwonder-21031641`, `Hiwonder-21031917`, `Hiwonder-21031920`, `Hiwonder-21031923`, `Hiwonder-21031618`, `Hiwonder-21031630`, `Hiwonder-21031642`, `Hiwonder-21031619`, `Hiwonder-21031631`, `Hiwonder-21031643`, `Hiwonder-21031620`, `Hiwonder-21031632`, `Hiwonder-21031644`, `Hiwonder-21031621`, `Hiwonder-21031633`, `Hiwonder-21031645`, `Hiwonder-21031918`, `Hiwonder-21031921`, `Hiwonder-21031924`, `Hiwonder-21031622`, `Hiwonder-21031634`, `Hiwonder-21031646`, `Hiwonder-21031623`, `Hiwonder-21031635`, `Hiwonder-21031647`, `Hiwonder-21031624`, `Hiwonder-21031636`, `Hiwonder-21031648`

**Model / revision scope:** LanderPi. Match the purchased option below; hardware revisions and controller images are not interchangeable.
{% endhint %}

![LanderPi — product image supplied by OpenELAB](../../.gitbook/assets/hiwonder-93.png)

## Product overview

LanderPi is a Raspberry Pi ROS2 mobile manipulator offered with Mecanum, Ackermann and tracked chassis. Its 45 options must be matched to the correct chassis, controller and kit configuration.

Set the chassis type before using the directional controls. Check camera calibration and arm zero offsets before attempting mobile grasping; navigation alone does not validate arm positioning.

### Models and purchasing options

| OpenELAB SKU        | Purchased option                                           |
| ------------------- | ---------------------------------------------------------- |
| `Hiwonder-21031613` | Starter Kit / Without Raspberry Pi 5 / Mecanum Chassis     |
| `Hiwonder-21031625` | Starter Kit / Without Raspberry Pi 5 / Ackerman Chassis    |
| `Hiwonder-21031637` | Starter Kit / Without Raspberry Pi 5 / Tank Chassis        |
| `Hiwonder-21031916` | Starter Kit / With Raspberry Pi 5 2GB / Mecanum Chassis    |
| `Hiwonder-21031919` | Starter Kit / With Raspberry Pi 5 2GB / Ackerman Chassis   |
| `Hiwonder-21031922` | Starter Kit / With Raspberry Pi 5 2GB / Tank Chassis       |
| `Hiwonder-21031614` | Starter Kit / With Raspberry Pi 5 4GB / Mecanum Chassis    |
| `Hiwonder-21031626` | Starter Kit / With Raspberry Pi 5 4GB / Ackerman Chassis   |
| `Hiwonder-21031638` | Starter Kit / With Raspberry Pi 5 4GB / Tank Chassis       |
| `Hiwonder-21031615` | Starter Kit / With Raspberry Pi 5 8GB / Mecanum Chassis    |
| `Hiwonder-21031627` | Starter Kit / With Raspberry Pi 5 8GB / Ackerman Chassis   |
| `Hiwonder-21031639` | Starter Kit / With Raspberry Pi 5 8GB / Tank Chassis       |
| `Hiwonder-21031616` | Starter Kit / With Raspberry Pi 5 16GB / Mecanum Chassis   |
| `Hiwonder-21031628` | Starter Kit / With Raspberry Pi 5 16GB / Ackerman Chassis  |
| `Hiwonder-21031640` | Starter Kit / With Raspberry Pi 5 16GB / Tank Chassis      |
| `Hiwonder-21031617` | Standard Kit / Without Raspberry Pi 5 / Mecanum Chassis    |
| `Hiwonder-21031629` | Standard Kit / Without Raspberry Pi 5 / Ackerman Chassis   |
| `Hiwonder-21031641` | Standard Kit / Without Raspberry Pi 5 / Tank Chassis       |
| `Hiwonder-21031917` | Standard Kit / With Raspberry Pi 5 2GB / Mecanum Chassis   |
| `Hiwonder-21031920` | Standard Kit / With Raspberry Pi 5 2GB / Ackerman Chassis  |
| `Hiwonder-21031923` | Standard Kit / With Raspberry Pi 5 2GB / Tank Chassis      |
| `Hiwonder-21031618` | Standard Kit / With Raspberry Pi 5 4GB / Mecanum Chassis   |
| `Hiwonder-21031630` | Standard Kit / With Raspberry Pi 5 4GB / Ackerman Chassis  |
| `Hiwonder-21031642` | Standard Kit / With Raspberry Pi 5 4GB / Tank Chassis      |
| `Hiwonder-21031619` | Standard Kit / With Raspberry Pi 5 8GB / Mecanum Chassis   |
| `Hiwonder-21031631` | Standard Kit / With Raspberry Pi 5 8GB / Ackerman Chassis  |
| `Hiwonder-21031643` | Standard Kit / With Raspberry Pi 5 8GB / Tank Chassis      |
| `Hiwonder-21031620` | Standard Kit / With Raspberry Pi 5 16GB / Mecanum Chassis  |
| `Hiwonder-21031632` | Standard Kit / With Raspberry Pi 5 16GB / Ackerman Chassis |
| `Hiwonder-21031644` | Standard Kit / With Raspberry Pi 5 16GB / Tank Chassis     |
| `Hiwonder-21031621` | Advanced Kit / Without Raspberry Pi 5 / Mecanum Chassis    |
| `Hiwonder-21031633` | Advanced Kit / Without Raspberry Pi 5 / Ackerman Chassis   |
| `Hiwonder-21031645` | Advanced Kit / Without Raspberry Pi 5 / Tank Chassis       |
| `Hiwonder-21031918` | Advanced Kit / With Raspberry Pi 5 2GB / Mecanum Chassis   |
| `Hiwonder-21031921` | Advanced Kit / With Raspberry Pi 5 2GB / Ackerman Chassis  |
| `Hiwonder-21031924` | Advanced Kit / With Raspberry Pi 5 2GB / Tank Chassis      |
| `Hiwonder-21031622` | Advanced Kit / With Raspberry Pi 5 4GB / Mecanum Chassis   |
| `Hiwonder-21031634` | Advanced Kit / With Raspberry Pi 5 4GB / Ackerman Chassis  |
| `Hiwonder-21031646` | Advanced Kit / With Raspberry Pi 5 4GB / Tank Chassis      |
| `Hiwonder-21031623` | Advanced Kit / With Raspberry Pi 5 8GB / Mecanum Chassis   |
| `Hiwonder-21031635` | Advanced Kit / With Raspberry Pi 5 8GB / Ackerman Chassis  |
| `Hiwonder-21031647` | Advanced Kit / With Raspberry Pi 5 8GB / Tank Chassis      |
| `Hiwonder-21031624` | Advanced Kit / With Raspberry Pi 5 16GB / Mecanum Chassis  |
| `Hiwonder-21031636` | Advanced Kit / With Raspberry Pi 5 16GB / Ackerman Chassis |
| `Hiwonder-21031648` | Advanced Kit / With Raspberry Pi 5 16GB / Tank Chassis     |

A separately named bracket, horn, chassis or rail is the listed accessory, not a complete robot or servo. A “without controller / Raspberry Pi / Jetson / micro:bit” option requires the matching controller separately. Check the selected option’s packing list before starting.

## Applications

Use LanderPi to learn manual motion, perception and staged automation. Start with an unloaded mechanism and the sensors actually included in the selected kit.

## Specifications

| Parameter  | Value / scope                                 |
| ---------- | --------------------------------------------- |
| Controller | Raspberry Pi 5 options                        |
| Chassis    | M1 Mecanum / A1 Ackermann / T1 tracked        |
| Arm        | Mobile manipulation configuration as selected |
| Sensors    | Depth camera and LiDAR vary by kit            |
| Power      | Use the supplied matching battery and charger |

Specifications: [manufacturer product data](https://www.hiwonder.com/products/landerpi) and [OpenELAB listing](https://openelab.io/products/landerpi-robot-car). Figures describe the stated configuration; accessory-only options do not inherit the complete kit specifications.

## Hardware and connections

Connect the supplied battery or adapter to the **robot’s designated power/expansion board**, not directly to a computer GPIO or an unverified charging socket. Inspect the camera, motor/servo and controller cables while power is off. Place the mobile base on a clear level floor, away from edges, and remove objects from any gripper.

Match the controller, camera, LiDAR and chassis configuration to the SKU. Optional voice/AI modules require their own cables and software. A USB camera, depth camera and CSI ribbon camera are not interchangeable interfaces.

## Software and development resources

Start with the factory image for **LanderPi and the exact controller option**. WonderPi is the documented initial control application. Use the official model downloads for restoration; a generic Raspberry Pi OS or JetPack installation does not include the robot services, calibrated offsets and device configuration.

For development, preserve a backup of the supplied image and calibration files before replacing software. Select the manual branch for the installed board and ROS generation. A menu or directory for a different product is not a compatible firmware target.

## Getting started

**Prerequisites:** the selected hardware, its matching power source, the required data cable, and a clear work area. Begin with the supplied firmware and an unloaded mechanism.

1. Match the SKU table to the physical controller and kit. For a controller-excluded option, install the supported board and its exact robot image before attempting the remaining steps.
2. Place the mobile base on a clear level floor, away from edges, and remove objects from any gripper. Inspect polarity and cable seating, then power the robot with the supplied matching power system.
3. Allow the onboard computer to finish booting and reach its documented ready posture/indicator state. Keep the mechanism clear because initialization may move servos.
4. Install **WonderPi** from the model’s official resources. Enable Wi-Fi and the local-network/location permissions required for discovery. Select **Advanced → LanderPi(M1), LanderPi(A1) or LanderPi(T1)**, then **+ → Direct Connection Mode**.
5. Join the robot’s **HW…** hotspot using **hiwonder** on an unchanged factory image. Stay connected if the phone reports no Internet; return to the app and refresh until the correct robot icon appears.
6. Open Robot/Remote Control and verify the camera image. Give a brief low-speed forward command, release it and confirm the base stops before testing a turn.
7. End the demonstration and shut down the onboard operating system before removing power. Keep the original image and configuration until basic control is repeatable.

**Expected result:** The correct robot is discovered, its live camera/connection status is visible, and one small manual command responds and stops predictably. Autonomous tasks and loaded motion remain subsequent tests.

Procedure reference: [official model or interface manual](https://wiki.hiwonder.com/projects/LanderPi/en/latest/docs/1_LanderPi_User_Manual.html). The steps above are a bounded initial check, not a substitute for the full assembly and development chapters.

## Troubleshooting and FAQs

**No hotspot:** wait for the full boot sequence, verify the battery/adapter and image/controller match, then check whether the robot was previously configured for LAN mode.

**Phone joins Wi-Fi but the app sees nothing:** remain on the robot network despite the no-Internet warning, grant local-network discovery permissions, select the correct model and refresh. The factory password may have been changed on a used unit.

**Camera works but motion is wrong:** stop immediately and verify the chassis type, motor/servo connections and model configuration. Do not compensate with unrelated servo offsets.

**Vision, mapping or voice option is unavailable:** check the selected kit’s actual camera, LiDAR and AI/voice modules. Offline local control does not establish that a cloud AI service is configured.

**Restoring firmware:** use the exact model/controller resource package and retain calibration files; do not write an image for a similarly named Pro or legacy version.

## Downloads and technical documents

* [Official user / interface manual](https://wiki.hiwonder.com/projects/LanderPi/en/latest/docs/1_LanderPi_User_Manual.html)
* [Manufacturer Hiwonder LanderPi ROS2 Robot Car Kit - 6DOF Arm & LiDAR specifications and option drawings](https://www.hiwonder.com/products/landerpi)

Use the manual’s download or appendix section for the matching revision. A linked download directory is not a claim that every firmware archive, CAD file or installer has been tested. Do not flash an image for a similarly named product.

## References and validation

* [OpenELAB product and SKU options](https://openelab.io/products/landerpi-robot-car).
* [Official user / interface manual](https://wiki.hiwonder.com/projects/LanderPi/en/latest/docs/1_LanderPi_User_Manual.html)
* [Manufacturer Hiwonder LanderPi ROS2 Robot Car Kit - 6DOF Arm & LiDAR specifications and option drawings](https://www.hiwonder.com/products/landerpi)

Reviewed against the linked sources on 19 November 2026. Software installation, compilation and physical hardware tests were not performed for this guide. Use the observable checkpoints above to verify your own unit before integrating it into a larger system.
