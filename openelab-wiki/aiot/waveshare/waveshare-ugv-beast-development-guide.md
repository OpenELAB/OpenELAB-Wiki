# Waveshare UGV Beast Engineering Guide

{% hint style="info" %}
[**View Waveshare UGV Beast on OpenELAB**](https://openelab.io/products/waveshare-ugv-beast-ros2-robot)

**Model/option:** Waveshare UGV Beast · **Top-200 SKU:** `Waveshare-28695`
{% endhint %}

[Waveshare-28695](https://openelab.io/products/waveshare-ugv-beast-ros2-robot)

## Product and scope

**28695 UGV Beast** is a tracked mobile-robot platform with Raspberry Pi host options and an ESP32 lower controller. Confirm the actual Pi, pan-tilt and software package; UGV Rover and different ROS kits have separate scopes.

## Hardware and technical documents

| Item                 | Reference                                                                   |
| -------------------- | --------------------------------------------------------------------------- |
| Locomotion           | Tracked off-road chassis                                                    |
| Control architecture | ESP32 handles low-level motor/control tasks; Raspberry Pi 4B/5 host options |
| Peripherals          | IMU, display, lighting and supported servo interfaces                       |
| Package options      | Host board and pan-tilt may be included or excluded                         |
| Applications         | Mobile perception and remote-control experiments                            |

The UGV-Beast wiki supplies **assembly, battery/power, wiring, host-image and controller resources**. Verify the actual battery/polarity and controller interface before starting. A store title mentioning ROS2 does not establish that every factory image runs the same ROS stack.

## Getting started

1. Check track/mechanical assembly and battery wiring, keeping the tracks clear of the bench.
2. Boot the manufacturer image matched to the installed Pi.
3. Establish the documented remote interface and inspect lower-controller communication.
4. Test a low-speed forward/stop sequence in a clear area.
5. Verify camera/pan-tilt separately, then install only the ROS workflow documented for the received kit.

**Expected checkpoint:** reliable low-level control and stop behavior with a working host-camera connection.

## Development software and recovery

Use the UGV-Beast manufacturer's source/firmware resources and preserve both Raspberry Pi image and ESP32 firmware revisions. Host and lower-controller recovery are separate. Do not flash a Rover lower-controller image merely because both robots use ESP32.

## FAQs

**The web UI works but motors do not?** Check lower-controller link, battery, power enable and selected chassis configuration.

**No camera?** Verify included camera and correct Pi image/driver.

**Can I run a generic ROS launch file?** Confirm topics, transforms and controller protocol first.

## Sources and validation

* [Official hardware/setup wiki](https://www.waveshare.com/wiki/UGV-Beast)
* [Manufacturer kit options](https://www.waveshare.com/product/ugv-beast.htm)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.

## Official documentation and development resources

Use [Introduction](https://www.waveshare.com/wiki/UGV-Beast) for the manufacturer's complete model reference, diagrams and maintained examples. The references below complement this guide's local instructions.

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
