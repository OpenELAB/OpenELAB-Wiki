---
description: MID, HAP, TELE, and AVIA LiDAR families and integration guides.
cover: ../../.gitbook/assets/livox-logo.jpg
coverY: 0
---

# Livox

Livox develops LiDAR sensors for 3D perception and mapping. Its product families include compact wide-field sensors for mobile robots and longer-range devices for mapping and forward perception.

[Browse Livox products on OpenELAB](https://openelab.io/collections/brands-livox)

### Popular product guides

Products in the OpenELAB Top200 net-sales snapshot for 17 August–17 November 2026, ordered by their original sales rank. Shared model-family guides appear once; match the exact model, SKU and purchased option. This dated sales order is separate from manufacturer website-traffic ranking.

| Product guide                                                                                           | Models / order codes                |
| ------------------------------------------------------------------------------------------------------- | ----------------------------------- |
| [Livox MID-360S 3D LiDAR Sensor Engineering Guide](livox-mid-360s-3d-lidar-sensor-engineering-guide.md) | Livox-MID-360S-Kit · Livox-MID-360S |
| [LIVOX MID-70 User Manual](livox-mid-70-user-manual.md)                                                 | Livox-MID-70                        |
| [Livox Avia 2 With-Fan LiDAR Engineering Guide](livox-avia-2-development-guide.md)                      | Livox-AVIA2                         |
| [Livox MID-360L LiDAR Engineering Guide](livox-mid-360l-development-guide.md)                           | Livox-MID-360L-Kit                  |

### Product range

* MID-series compact 3D LiDAR sensors
* HAP automotive-oriented LiDAR and TELE long-range sensing
* AVIA-family mapping sensors, connection accessories, and visualization tools

### Product families and examples

| Product     | Typical use                            | Links                                                                                                                              |
| ----------- | -------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| MID-360S    | Compact 360-degree robotic SLAM        | [Wiki guide](livox-mid-360s-3d-lidar-sensor-engineering-guide.md) · [OpenELAB product](https://openelab.io/products/livox-mid360)  |
| HAP T1 / TX | Forward perception and HAP integration | [HAP T1 manual](livox-hap-t1-user-manual.md) · [OpenELAB product](https://openelab.io/products/livox-hap-automotive-grade-lidar3d) |
| MID-360L    | AMR and autonomous-forklift perception | [OpenELAB product](https://openelab.io/products/livox-mid-360l-3d-lidar)                                                           |
| MID-70      | Wide-angle mobile-robot sensing        | [Wiki guide](livox-mid-70-user-manual.md) · [OpenELAB product](https://openelab.io/products/livox-mid-70-compact-lidar3d)          |

### Popular applications

* Build LiDAR-based SLAM and localization for mobile robots.
* Capture point clouds for mapping and spatial measurement.
* Evaluate 3D obstacle detection and forward-perception systems.

HAP T1 and TX have separate manuals. Select the manual for your variant; the complete documentation index also includes legacy Livox models.

### Manufacturer resources

* [Livox](https://www.livoxtech.com/)
* [Livox downloads](https://www.livoxtech.com/downloads)

### More manuals and tutorials

<details>

<summary>Browse 9 additional guides</summary>

* [LIVOX Mid-360S User Manual](livox-mid-360s-user-manual.md)
* [LIVOX AVIA User Manual](livox-avia-user-manual.md)
* [LIVOX TELE-15 User Manual](livox-tele-15-user-manual.md)
* [LIVOX Viewer 2 User Manual](livox-viewer-2-user-manual.md)
* [LIVOX HUB User Manual](livox-hub-user-manual.md)
* [LIVOX Mid-360 User Manual](livox-mid-360-user-manual.md)
* [LIVOX HAP(T1) User Manual](livox-hap-t1-user-manual.md)
* [LIVOX HAP (TX) User Manual](livox-hap-tx-user-manual.md)
* [LIVOX Mid Series User Manual](livox-mid-series-user-manual.md)

</details>

[Explore Robotics documentation](../robotics-wiki-home-page.md) · [OpenELAB Wiki home](../../)

### Model-specific protocol and development references

Choose [MID-360S sensor or kit](livox-mid-360s-3d-lidar-sensor-engineering-guide.md), [MID-360L](livox-mid-360l-development-guide.md), [Avia 2](livox-avia-2-development-guide.md) or [MID-70](livox-mid-70-user-manual.md) by the purchased model. The guides distinguish first-generation SDK/Viewer/ROS1 from SDK2/Viewer2 and model-specific ROS support. They add packet and command fields, configuration keys, callback/message contracts, time synchronization, recording/replay, diagnostics and observable first-result checks. Reserved S/L pins and model-specific upgrade identities remain explicitly bounded.

Source review and static validation are distinct from executing an SDK or commissioning physical hardware. Follow each guide’s stated evidence and validation limits.
