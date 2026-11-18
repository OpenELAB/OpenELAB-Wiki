# Hiwonder ROSOrin and ROSOrin Pro Engineering Guide

{% hint style="info" %}
[**View Hiwonder ROSOrin and ROSOrin Pro (Pro) on OpenELAB**](https://openelab.io/products/hiwonder-rosorin-pro-smart-car) · [**View Hiwonder ROSOrin and ROSOrin Pro (standard) on OpenELAB**](https://openelab.io/products/hiwonder-rosorin-smart-car)

**Model/family:** Hiwonder ROSOrin and ROSOrin Pro · **OpenELAB SKUs:** `Hiwonder-21031913`, `Hiwonder-21031729` · Confirm exact purchased model and option before following wiring/firmware instructions.
{% endhint %}

[Hiwonder-21031913](https://openelab.io/products/hiwonder-rosorin-pro-smart-car) · [Hiwonder-21031729](https://openelab.io/products/hiwonder-rosorin-smart-car)

## Product and scope

ROSOrin and ROSOrin Pro are related ROS2 mobile-robot platforms, with separate chassis/manipulation packages and Jetson/Raspberry Pi options. This page explicitly covers **21031729 ROSOrin** and **21031913 ROSOrin Pro**; select each model's manual and host branch.

## Hardware and technical documents

| Item        | Reference                                                      |
| ----------- | -------------------------------------------------------------- |
| ROSOrin     | Mecanum mobile platform with LiDAR/vision/audio options        |
| ROSOrin Pro | Mobile manipulation configuration with arm, depending on kit   |
| Hosts       | Jetson / Raspberry Pi variants; image-specific support         |
| Software    | Manufacturer ROS2 image, robot control and perception examples |

Use each official model page for the **kit inventory, dimensions and electrical specification**, and the corresponding user manual for connector diagrams. An arm or depth camera shown in a family photograph is not proof it is included in every package.

## Getting started

1. Verify model, host, battery and all fitted peripherals against the order. Keep wheels restrained and the arm unloaded initially.
2. Boot the matching factory image and use the documented WonderAi/remote-access route.
3. Record OS, ROS distribution, controller and sensor configuration.
4. Test stop and low-speed chassis motion first. On Pro, calibrate/test the arm separately.
5. Verify camera and LiDAR visualization before running navigation or network-dependent AI demonstrations.

**Expected checkpoint:** correct chassis direction, a reliable stop, and stable sensor streams; Pro arm motion must also pass its own calibration check.

## Development software and recovery

Use the model-specific manufacturer repository/manual, including **Hiwonder/ROSOrin-Pro** for Pro. Preserve image, launch configuration and calibration versions. Restore the appropriate image when recovering the host; motor/controller firmware requires its own procedure.

## FAQs

**Can the Pro image be used on the non-Pro?** Only if Hiwonder explicitly supports that hardware combination.

**LLM demo cannot connect?** Check backend, credentials, network and microphone independently of motor control.

**Navigation behaves incorrectly?** Inspect odometry, transforms and installed LiDAR selection before tuning parameters.

## Sources and validation

* [ROSOrin product and tutorial route](https://www.hiwonder.com/products/rosorin)
* [ROSOrin host-specific docs](https://docs.hiwonder.com/projects/ROSOrin/en/jetson-orin-nano-version/)
* [ROSOrin Pro product](https://www.hiwonder.com/products/rosorin-pro)
* [ROSOrin Pro manual](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/)
* [ROSOrin Pro code](https://github.com/Hiwonder/ROSOrin-Pro)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
