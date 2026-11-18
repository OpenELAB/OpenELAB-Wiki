# Hiwonder ROSpider Engineering Guide

{% hint style="info" %}
[**View Hiwonder ROSpider on OpenELAB**](https://openelab.io/products/rospider-ros2)

**Model/family:** Hiwonder ROSpider · **OpenELAB SKU:** `Hiwonder-21060103`
{% endhint %}

[Hiwonder-21060103](https://openelab.io/products/rospider-ros2)

## Product and scope

**ROSpider** is a ROS hexapod platform with controller and kit options. OpenELAB **Hiwonder-21060103** is advertised with 3D vision and an arm; verify its fitted host and perception package before using a tutorial. SpiderPi/SpiderPi Pro are separate products.

## Hardware and technical documents

| Item                      | Reference                                                   |
| ------------------------- | ----------------------------------------------------------- |
| Locomotion                | Six-legged, bus-servo platform                              |
| Host variants             | Jetson and Raspberry Pi packages                            |
| Documented ROS2 reference | Ubuntu 22.04 / ROS2 Humble in the cited ROSpider manual     |
| Expansion                 | Camera, LiDAR, arm and audio depend on the selected package |

The manufacturer's **ROSpider User Manual** contains assembly, port diagrams and kit inventories. Use the branch for the actual host. Detailed electrical ratings and mounting geometry come from that branch's hardware resources, not from a generic hexapod diagram.

## Getting started

1. Support the body so the legs can move without carrying or striking a load. Check servo connections with power off.
2. Boot the matching delivered image and use the manual's remote-access procedure.
3. Identify the controller, servo bus, camera and LiDAR. Save their configuration.
4. Test one documented stationary posture at conservative speed; verify the stop behavior.
5. Then test a short gait in a clear area before enabling mapping, arm actions or vision behaviors.

**Expected checkpoint:** stable posture and controlled short movement with all expected joints/sensors visible.

## Development software and recovery

The official **Hiwonder/ROSpider** repository and manual supply application code and ROS workflows. Retain the exact image, repository branch and calibration/action data. A controller update and a Linux-image update are different operations. Restore from the matching official image if system changes break startup.

## FAQs

**Why does the tutorial show different hardware?** ROSpider has multiple host and kit versions; change the documentation branch.

**A leg moves incorrectly?** Stop and verify servo IDs, mounting orientation and calibration.

**No LiDAR or depth camera?** Check whether that accessory is included and its driver matches the actual model.

## Sources and validation

* [Manufacturer model page](https://www.hiwonder.com/products/rospider)
* [Host-specific manual](https://docs.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/)
* [Software repository](https://github.com/Hiwonder/ROSpider)
* [Current ROSpider user manual](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/1_ROSpider_User_Manual.html)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
