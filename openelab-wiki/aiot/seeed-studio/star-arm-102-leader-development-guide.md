# Seeed Studio Star Arm 102 Leader Arm Development Guide

[Product at OpenELAB](https://openelab.io/products/seeed-studio-rebot-arm-b601-dm-leader-arm) · [Seeed Studio hub](./)

### Product role and scope

The **Star Arm 102**, Seeed ordering code **100004723**, is the leader arm used to command a reBot B601-DM or B601-RS follower. Use it for teleoperation practice, demonstration collection and robot-learning experiments. A leader device records the operator's intended joint movement; it is not a replacement for the follower's actuators, controller or power system.

| Item                   | Development relevance                                                 |
| ---------------------- | --------------------------------------------------------------------- |
| Structure              | Manufacturer describes 6+1 degrees of freedom                         |
| Ecosystems             | Seeed robot-learning workflow, ROS2 and LeRobot                       |
| Host connection        | Bind the actual leader serial interface in the selected application   |
| Leader power           | Seeed's teleoperation checklist specifies a separate 12V / 2A adapter |
| Follower compatibility | B601-DM and B601-RS require their own model-specific configuration    |
| Package scope          | Check the order for adapter, mounting hardware and cables             |

Use the manufacturer's product resource links for the current hardware/CAD package. Confirm dimensions and mounting geometry from that package before making a fixture; dimensions are not inferred from photographs.

### Getting started: leader recognition before follower movement

1. Secure the leader and follower to the bench. Keep the follower's workspace clear and make its power isolation accessible.
2. Identify the leader, follower and any USB-CAN adapters by unplug/replug comparison. On Linux, inspect persistent device names:

```bash
ls -l /dev/serial/by-id/
```

3. Install the Seeed-supported robotics software using its current instructions. Bind the leader to the correct serial device and select the actual DM or RS follower profile.
4. Perform the application-guided leader and follower calibration. Keep calibration records paired with the corresponding devices.
5. First verify leader joint readings without commanding motion. Then perform the official low-speed teleoperation check, with no payload and sufficient clearance.

**Checkpoint:** the application identifies both devices and small leader motions map to the expected follower joints without jumps or reversed motion. Stop if IDs, limits or calibration fail.

### Development software and data

SenseCraft Robotics provides a guided setup path. The linked Seeed tutorial connects hardware preparation to camera binding, teleoperation and later dataset collection. Use the matching robot implementation when moving into LeRobot; do not combine a generic SO-ARM configuration with a B601 follower.

Record software version, serial bindings, calibration files and camera configuration with each dataset. Successful teleoperation alone does not validate camera synchronization or training-data quality.

### FAQs

**Can the leader use the follower supply?** Use the documented leader adapter. DM and RS followers have separate power requirements.

**Devices swap after reboot?** Prefer persistent serial identities where available; recheck adapter mapping before enabling motion.

**Calibration fails or movement is reversed?** Check model selection, joint IDs, cabling and saved calibration. Do not compensate by manually changing limits until the identity mismatch is understood.

**Is the full CAD or protocol reproduced here?** No. The manufacturer's current resource package is the technical reference; verify its revision before fabrication.

### Sources and validation

* [Star Arm 102 manufacturer product and resource links](https://www.seeedstudio.com/Star-Arm-102-p-6765.html)
* [Seeed hardware and teleoperation workflow](https://wiki.seeedstudio.com/robotics/paper_reading_hardware_and_teleoperation/)
* [SenseCraft Robotics](https://sensecraft.seeed.cc/en/robotics)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
