# Elephant Robotics myAGV 2023 Pi: image matching and navigation bring-up

{% hint style="info" %}
[**View Elephant Robotics myAGV 2023 Pi on OpenELAB**](https://openelab.io/products/elephant-robotics-myagv-rpi-robot-kit-mapping-autonomous-navigation)

**Model:** myAGV 2023 Pi (Raspberry Pi controller configuration) · **Top-200 SKU:** `MyAGV-2023-PI` · **Observed storefront SKU:** `MyAGV-2023-Pi` (capitalization variation). Verify the supplied image, host and peripherals before loading a ROS stack or running motors.
{% endhint %}

[MyAGV-2023-PI](https://openelab.de/products/elephant-robotics-myagv-rpi-roboter)

## Product and scope

The Raspberry Pi version of myAGV 2023 is a mobile robotics platform for mapping, navigation and education. This page covers MyAGV-2023-PI. Original myAGV, Jetson variants and later platforms require their own images and firmware.

## Hardware and technical documents

| Item                           | Reference                                                                         |
| ------------------------------ | --------------------------------------------------------------------------------- |
| Compute                        | Raspberry Pi 4B                                                                   |
| Manufacturer software baseline | Customized Ubuntu MATE 20.04; preserve the shipped image before upgrades          |
| Perception                     | Manufacturer describes a 360° LiDAR                                               |
| Payload reference              | Manufacturer lists 5,000 g; verify actual mounting and operating conditions       |
| Version example                | Image v1.0.25.04.22 pairs with firmware v1.1 and myagv\_ros\_2023pi tag v1.1.0-pi |

Use the myagv\_pi23\_en manual tree for assembly, battery/charging, interfaces, motion control and downloads. Inventory the actual Pi, LiDAR and accessories; optional depth cameras or arms are not established by the base SKU. Keep a clear floor area and an accessible stop/power disconnect for motion tests.

## Getting started

1. Record the physical model, controller firmware and system image. On the factory system, inspect /etc/version and archive the result with a storage backup.
2. Use the manufacturer system-image compatibility table before replacing the SD image. Do not install a Jetson image or mix an old firmware with a newer unmatched ROS package.
3. Verify local access and the documented LiDAR/serial devices before starting motion services. Confirm battery condition and sensor cable seating.
4. Use the exact Pi manual's keyboard/gamepad motion tutorial at low speed in an open area. Confirm forward, lateral and turning directions, then test stopping.
5. Run the manual's mapping workflow, inspect scan/odometry consistency and save a small map. Test one nearby navigation goal before larger autonomous routes.

**Expected checkpoint:** Controlled motion and stopping, a stable LiDAR display, and a saved map with the image/firmware/ROS versions recorded.

## Development software and recovery

Use the official Pi 2023 documentation and matching ROS package tag. Navigation launch files depend on that software combination; this guide avoids transplanting commands from another chassis version. Diagnose hardware motion, odometry, scans and localization separately. Restore the saved compatible image if a general OS update breaks drivers.

## FAQs

**Can I upgrade Ubuntu independently?** First check vendor support and preserve recovery media; the supplied robot environment depends on its kernel, drivers and ROS packages.

**The scan is visible but navigation is unstable.** Check timestamps, odometry, frame transforms, localization and the physical test surface before changing planners.

**Can I immediately carry the maximum advertised payload?** Validate mounting, balance, clearance and stopping with the actual load.

## Sources and validation

* [Elephant Robotics myAGV Pi 2023 overview](https://www.elephantrobotics.com/en/myagv-2023-pi-en/)
* [Pi 2023 documentation](https://docs.elephantrobotics.com/docs/myagv_pi23_en/)
* [Image and firmware compatibility table](https://docs.elephantrobotics.com/docs/myagv_pi23_en/8-FilesDownload/8.4-SystemInformation/8.4.1-System_Image.html)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
