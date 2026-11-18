# Hiwonder JetRover Engineering Guide

[Hiwonder-21030861](https://openelab.io/products/hiwonder-jetrover-ai-car)

### Product and scope

JetRover is a composite mobile-manipulation platform. **Hiwonder-21030861** must be matched to the ordered controller and chassis; JetRover supports multiple host and mobility configurations rather than one universal image.

### Hardware and technical documents

| Item              | Reference                                                |
| ----------------- | -------------------------------------------------------- |
| Mobility variants | Mecanum, Ackermann and tracked chassis                   |
| Manipulation      | Six-DoF arm in the documented platform                   |
| Host              | Jetson or Raspberry Pi configurations                    |
| Perception        | LiDAR and depth-camera package options                   |
| Applications      | Navigation, perception and mobile-manipulation education |

The manufacturer's portal links **schematics, source, system images, tutorials and experiment resources**. Use the actual chassis assembly and motor layout. The kinematic model for Ackermann steering differs from an omnidirectional chassis.

### Getting started

1. Verify chassis type, host, supply/battery and fitted peripherals. Keep the robot stationary and the arm unloaded.
2. Start from the corresponding factory image and follow its remote-desktop setup.
3. Inspect sensor streams and controller communication before motion.
4. Run the documented manual-control test at low speed, then check the stop command.
5. Use the matching chassis odometry and mapping tutorial. Test arm motion independently before combining navigation and grasping.

**Expected checkpoint:** predictable motion for the fitted chassis, coherent odometry and live perception streams.

### Development software and recovery

Follow the official JetRover documentation branch for the installed host and ROS generation. Preserve launch files, image revision and calibration before upgrades. For recovery, use that branch's image and controller firmware; a JetRover name match alone does not establish compatibility.

### FAQs

**Why does the robot move sideways unexpectedly?** Confirm selected chassis model and wheel/motor mapping.

**A ROS1 command fails?** Verify the installed ROS generation and use the matching tutorial.

**Can I reuse an arm action during navigation?** First confirm payload, clearance, stability and coordinate transforms on a stationary robot.

### Sources and validation

* [Manufacturer product and kit options](https://www.hiwonder.com/products/jetrover)
* [Official documentation and resource links](https://docs.hiwonder.com/projects/JetRover/en/jetson-orin-nano/)
* [LiDAR integration tutorial](https://docs.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/3.Lidar_Course.html)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
