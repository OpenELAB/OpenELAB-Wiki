# LDROBOT D800 and STL-27L Engineering Guide

[LDROBOT-D800](https://openelab.io/products/ldrobot-d800-dtof-lidar-kit)

### Product and scope

**D800** is the developer-kit configuration built around **STL-27L** planar DTOF LiDAR. The sensor and kit accessory package are separate scopes. Use it for 2D mapping and obstacle-perception experiments.

### Hardware and technical documents

| Item                    | Reference                                              |
| ----------------------- | ------------------------------------------------------ |
| Range                   | 0.03–25m in the manufacturer sensor catalogue          |
| Scan                    | 360°; typical 10Hz, adjustable documented range 6–13Hz |
| Ranging rate            | 21,600 measurements/s                                  |
| Ambient-light reference | 60,000lux                                              |
| Host connection         | Use the kit's documented UART/adapter path             |

Use the **STL-27L integration guide** linked from the product resources for supply, logic levels, pinout, dimensions and scan configuration. Do not wire the bare sensor as though its UART were an RS232 port.

### Getting started

1. Identify STL-27L and the supplied developer adapter/cable.
2. Follow its integration guide for power and data wiring; connect the documented adapter to the host.
3. Verify host interface enumeration and the manual's serial settings.
4. Use software explicitly supporting **STL-27L/D800** to inspect a scan.
5. Check a stationary target and scan orientation before passing data to SLAM.

**Expected checkpoint:** coherent planar scans from the actual sensor without sustained packet errors.

### Development software and recovery

Compatibility needs care: the reviewed **ldrobotSensorTeam/ldlidar\_sdk README lists LD06, LD19, LD14 and LD14P, but not STL-27L**. Do not claim that generic SDK supports D800 without confirmation. Use the STL-27L-specific package/integration files supplied for this kit; preserve their version and protocol reference.

### FAQs

**Can I use an LD19 launch file?** Only after confirming STL-27L packet format and driver support.

**No scan despite power?** Check supply, interface levels, serial settings, connector seating and model support.

**Is 25m universal?** Apply the sensor's target/illumination conditions and evaluate your environment.

### Sources and validation

* [Manufacturer STL-27L sensor catalogue](https://www.ldrobot.com/sensors)
* [Kit-specific integration and ROS2 resources](https://openelab.io/products/ldrobot-d800-dtof-lidar-kit)
* [Official generic SDK support table](https://github.com/ldrobotSensorTeam/ldlidar_sdk)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
