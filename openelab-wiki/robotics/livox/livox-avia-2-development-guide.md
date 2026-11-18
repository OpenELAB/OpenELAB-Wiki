# Livox Avia 2 With-Fan LiDAR Engineering Guide

{% hint style="info" %}
[**View Livox Avia 2 with fan on OpenELAB**](https://openelab.io/products/livox-avia2-fiber-laser-lidar)

**Exact model:** Livox Avia 2 (with fan) · **OpenELAB SKU:** `Livox-AVIA2` · **Variant:** choose the with-fan option; Avia 2 NF is different hardware.
{% endhint %}

[Product at OpenELAB](https://openelab.de/products/livox-avia2-lidar-luefter) · [Livox hub](./)

## Product and applications

This page covers the **Livox Avia 2 with fan**, OpenELAB **Livox-AVIA2**. It is a long-range 3D LiDAR for infrastructure monitoring, volumetric measurement and distant-target perception. Avia, Avia 2 and Avia 2 NF are separate hardware scopes.

## Key specifications

| Item               | Avia 2                                                                                          |
| ------------------ | ----------------------------------------------------------------------------------------------- |
| Laser              | 1535nm; Class 1 under the cited IEC standard                                                    |
| Normal mode        | 80° × 80° FOV; 350,000 points/s                                                                 |
| Focus mode         | 15° × 15° FOV; 100,000 points/s                                                                 |
| Documented ranging | Normal: 400m at 5% reflectivity; Focus: ≥800m at 10% reflectivity, under stated test conditions |
| Blind zone         | 5m at 80% reflectivity                                                                          |
| Power input        | 9–27V DC; allow for the documented 55W startup/extreme-temperature demand                       |
| Data               | 100Mbps Ethernet                                                                                |
| Timing             | PPS + GPRMC, PTP and NTP                                                                        |
| With-fan envelope  | 146 × 113 × 139mm; ≤1.8kg                                                                       |
| Protection         | IP66; operating temperature −20 to 65°C                                                         |

Use the specifications page for accuracy definitions, test conditions and thermal restrictions. Maximum cutoff range is not a guaranteed range for every surface or weather condition.

## Technical documents and software

The model-specific Downloads page provides the **Avia 2 User Manual**, product information, Viewer 2 for Windows/Linux, firmware/release notes, the sensor CAD model, FOV model and breakout-cable CAD. Select the with-fan model's files; do not substitute NF geometry.

Viewer 2 is the first bring-up path. Before adopting SDK2 or a ROS driver, confirm the chosen release explicitly supports **Avia 2** and its firmware. The public SDK2 repository's general description names older supported models; a Livox brand match alone is insufficient evidence of Avia 2 support. No unverified ROS launch command is supplied here.

## Getting started: acquire a live cloud

1. Mount the sensor securely with the fan unobstructed. Check the manual's connector orientation, pinout and recommended supply sizing before energizing.
2. Connect the correct breakout cable, Ethernet and regulated supply. Use a dedicated wired network for initial testing.
3. Install the Avia 2-compatible Viewer 2 from its Downloads page. Set the host network according to the manual rather than copying a MID-360 configuration.
4. Discover the unit, read its model/serial/firmware and start a point-cloud display. Select Normal mode first.
5. Observe a static target beyond the blind zone. Save a short recording and its mode/timing configuration.

**Expected result:** continuous point-cloud updates from the correct sensor, with coherent static geometry. Check packet reception and timestamps before integrating mapping software.

## Troubleshooting

**No device discovery:** inspect supply under load, Ethernet link, host subnet, firewall and the selected network adapter.

**Near objects are missing:** account for the documented blind zone; do not diagnose it as packet loss.

**The cloud rate changes:** verify Normal versus Focus mode and the return settings.

**Can it replace a safety scanner?** Validate the complete application and required certifications separately; a ranging sensor is not automatically a safety system.

## Sources and validation

* [Avia 2 manufacturer specifications](https://www.livoxtech.com/avia-2/specs)
* [Avia 2 manuals, Viewer 2, firmware and CAD](https://www.livoxtech.com/avia-2/downloads)
* [Avia 2 application and operating notes](https://www.livoxtech.com/avia-2)
* [Avia 2 FAQ](https://www.livoxtech.com/avia-2/faq)
* [Official Livox SDK2 repository; check explicit model support](https://github.com/Livox-SDK/Livox-SDK2)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
