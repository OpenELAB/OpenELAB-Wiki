# RoboSense Airy Lite LiDAR Engineering Guide

[RS-Airy-Lite](https://openelab.io/products/robosense-airy-lite-lidar-compact360)

### Product and scope

**Airy Lite** is a compact 3D LiDAR for mobile-robot blind-spot perception and mapping inputs. It is a separate model from Airy 96; their packet decoding, field of view and limits must not be interchanged.

### Hardware and technical documents

| Item          | Reference                                                |
| ------------- | -------------------------------------------------------- |
| Data          | 100BASE-TX Ethernet; UDP packets                         |
| Output        | 144,000 points/s at the documented 10Hz mode             |
| Supply        | 9–24V                                                    |
| Typical power | 6W under manufacturer test conditions                    |
| Body          | 65 × 64 × 72.5mm including cable outlet; under 250g      |
| Protection    | IP67; −20 to 60°C operating range in the cited reference |

The official **Airy Lite product manual** contains mechanical/FOV diagrams, connector wiring, packet information and operating-condition notes. Preserve that manual's revision and use its cable/power diagram before energizing.

### Getting started

1. Mount the sensor securely and connect the correct regulated supply/cable with power off.
2. Connect a dedicated Ethernet interface and set the host subnet according to the Airy Lite manual.
3. Install a **RoboSense driver release explicitly supporting Airy Lite**.
4. Select its model-specific configuration, verify packet reception and display the cloud.
5. Record a static scene and check sensor identity, timestamps and coordinate orientation.

**Expected checkpoint:** a coherent continuously updating cloud from the correct model, without sustained packet loss.

### Development software and recovery

The manufacturer links **rslidar\_sdk**, **rs\_driver** and ROS2 message dependencies. Match model support, ROS version and firmware; retain the source commit/configuration. Use the manual's firmware/recovery procedure instead of an Airy 96 image.

### FAQs

**Why are there occasional angular gaps?** The Airy Lite manual documents scan-pattern behavior; compare it with packet-loss diagnostics.

**No cloud though Ethernet is up?** Check subnet, destination settings, firewall, decoder/model and actual packet reception.

**Is maximum range guaranteed on every surface?** Apply the manufacturer's reflectivity, illumination and accuracy conditions.

### Sources and validation

* [Exact manufacturer manual](https://robosense-robotics.github.io/product-manual/en/AiryLite/)
* [Official ROS SDK](https://github.com/RoboSense-LiDAR/rsLiDAR_sdk)
* [Low-level driver](https://github.com/RoboSense-LiDAR/rs_driver)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
