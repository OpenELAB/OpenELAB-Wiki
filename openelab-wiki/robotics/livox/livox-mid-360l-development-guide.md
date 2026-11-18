# Livox MID-360L LiDAR Engineering Guide

{% hint style="info" %}
[**View Livox MID-360L LiDAR on OpenELAB**](https://openelab.io/products/livox-mid-360l-3d-lidar)

**Model:** Livox MID-360L · **Workbook SKU:** `Livox-MID-360L-Kit` · **Observed storefront SKU:** `Livox-MID-360L` (sensor). **Kit match not yet verified:** confirm whether the splitter cable/power adapter is included before following a kit-specific setup. MID-360L firmware and wiring must not be substituted with MID-360S or MID-360 versions.
{% endhint %}

[Livox-MID-360L-Kit](https://openelab.de/products/livox-mid-360l-3d-lidar)

## Product and scope

This guide covers **MID-360L**, including the OpenELAB kit row. **MID-360, MID-360S and MID-360L are distinct models.** Verify the actual kit's cable/converter/supply contents rather than importing another model's accessories.

## Hardware and technical documents

| Item                   | Reference                                                    |
| ---------------------- | ------------------------------------------------------------ |
| FOV                    | 360° horizontal; typical −10° to +34° vertical               |
| Output                 | 100,000 points/s, first return; typical 10Hz                 |
| Ranging reference      | 45m at 10% reflectivity; 100m cutoff under stated conditions |
| Close blind zone       | 0.1m                                                         |
| Supply / typical power | 12–27V DC / 4.2W                                             |
| Data / body            | 100BASE-TX; 65 × 65 × 63mm; IP67                             |

The **MID-360L Downloads** page provides the model-specific **User Manual (14 October 2026), product information, 3D and FOV models, firmware/release notes and Viewer 2**. Use these files for mechanical and connector integration.

## Getting started

1. Confirm the L model, inspect its cable pinout and use a correctly sized regulated supply.
2. Connect Ethernet and configure the host network using the L manual.
3. Install the model-compatible Viewer 2 from its Downloads page.
4. Discover the sensor and read model/serial/firmware before enabling the cloud.
5. Record a short static scene and inspect cloud continuity, timestamp source and orientation.

**Expected checkpoint:** a coherent live cloud from an identified MID-360L.

## Development software and recovery

The reviewed downloads list firmware **41.52.00.03**. Preserve the firmware/Viewer versions. Before using SDK2 or a ROS driver, confirm **MID-360L** is explicitly supported by that release; MID-360 support is not enough. Use only L-specific firmware and recovery instructions.

## FAQs

**Can I reuse MID-360S voltage/pin assumptions?** Verify the L manual separately.

**No sensor found?** Check supply, link, subnet, firewall and chosen network adapter.

**Are kit contents fixed by this page?** The sensor guide does not replace the exact order's packing list.

## Sources and validation

* [Exact specifications](https://www.livoxtech.com/mid-360l/specs)
* [Manual, firmware, CAD and Viewer](https://www.livoxtech.com/mid-360l/downloads)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
