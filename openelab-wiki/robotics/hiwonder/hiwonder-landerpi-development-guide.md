# Hiwonder LanderPi Engineering Guide

{% hint style="info" %}
[**View Hiwonder LanderPi on OpenELAB**](https://openelab.io/products/landerpi-robot-car)

**Model/option:** Hiwonder LanderPi · **OpenELAB SKU:** `Hiwonder-21031623`
{% endhint %}

[Hiwonder-21031623](https://openelab.io/products/landerpi-robot-car)

## Product and scope

**LanderPi**, OpenELAB **21031623**, combines a Raspberry Pi mobile base, arm and perception hardware for ROS development. Confirm the kit's Pi generation, LiDAR and camera; do not select a driver from an older LanderPi photograph.

## Hardware and technical documents

| Item          | Reference                                            |
| ------------- | ---------------------------------------------------- |
| Platform      | Raspberry Pi mobile-manipulation kit                 |
| Arm           | Six-DoF configuration in the OpenELAB listing        |
| Perception    | Model-dependent LiDAR and camera                     |
| Control paths | Manufacturer app, remote desktop and ROS development |
| Applications  | Mapping, navigation and vision-guided manipulation   |

The model's **User Manual** supplies assembly, connection diagrams and software resources. Use the actual LiDAR label and the documented type-selection tool when a sensor revision changes. Verify power/charging specifications from the supplied equipment and manual.

## Getting started

1. Check mechanical assembly and wiring with power off; restrain the wheels for first startup and unload the arm.
2. Boot the supplied image and connect using the manual's Wi-Fi/app or remote-desktop workflow.
3. Verify the actual LiDAR selection and serial connection; then inspect camera and scan data separately.
4. Test low-speed manual control and a small arm action, confirming stop behavior.
5. Run a short mapping test only after odometry and scan orientation are correct.

**Expected checkpoint:** controlled movement, live scan/camera data and an arm that moves predictably in the configured coordinate frame.

## Development software and recovery

Use the LanderPi image, source and tutorials matching the received hardware. Save image version, sensor model selections, serial mapping and calibration. Restore the supported system image for host recovery; changing a LiDAR driver cannot repair a poor cable connection.

## FAQs

**LiDAR has power but no serial data?** Check both cable ends, interface enumeration, permissions and the selected model.

**One arm joint does not respond?** With power off, inspect cabling and follow the manual's isolated joint check.

**Can another Hiwonder robot image be used?** Use a LanderPi-supported image with the correct controller/sensor configuration.

## Sources and validation

* [Manufacturer product](https://www.hiwonder.com/products/landerpi)
* [Official user manual and tutorial navigation](https://wiki.hiwonder.com/projects/LanderPi/en/latest/docs/1_LanderPi_User_Manual.html)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
