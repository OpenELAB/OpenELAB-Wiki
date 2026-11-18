# Seeed SO-101 Pro Servo Motor Kit: assembly and role configuration

{% hint style="info" %}
[**View Seeed SO-101 Pro Servo Motor Kit: assembly and role configuration on OpenELAB**](https://openelab.io/products/seeed-studio-so-101-pro-servo-motor-kit-lerobot)

**Model/variant:** Seeed SO-101 Pro Servo Motor Kit: assembly and role configuration · **OpenELAB SKU:** `Seeed-114993667` · Match the model and gear/ID to the leader or follower arm before installation.
{% endhint %}

[Seeed-114993667](https://openelab.io/products/seeed-studio-so-101-pro-servo-motor-kit-lerobot)

## Product and scope

Seeed 114993667 is the SO-101 Pro Servo Motor Kit for building a LeRobot arm system. It is distinct from a complete assembled arm and from a skeleton-only kit. Use it for teleoperation, demonstration collection and robot-learning projects after mechanical assembly.

## Hardware and technical documents

| Item                    | Reference                                                                     |
| ----------------------- | ----------------------------------------------------------------------------- |
| Part identification     | 114993667: Pro Motor Kit; 114993666: Basic Motor Kit; 114993668: skeleton kit |
| Pro-edition supply rule | Leader: 5 V; follower: 12 V, throughout setup, calibration and operation      |
| Control                 | USB servo-controller workflow with LeRobot SO-101                             |
| Mechanical resources    | SO-101-specific CAD/BOM and Seeed assembly guide                              |

Check the delivered BOM for servo models, reduction ratios, controller boards, cables and supplies. Printed structures, cameras and other accessories are not implied by the term motor kit. Do not swap the Pro leader and follower supplies. The Seeed SO-Arm tutorial contains specifications, wiring, servo configuration and assembly references; its voltage rule applies to the Seeed Pro configuration, not every SO-101 sold elsewhere.

## Getting started

1. Separate and label leader/follower servos and supplies before assembly. Cross-check part markings against Seeed's Pro-edition table.
2. Follow the servo ID and middle-position setup with one unconfigured servo connected at a time. Keep the required supply connected as directed; USB alone does not prove the servo is powered.
3. Assemble the SO-101 structure using the matching CAD and orientation diagrams. Check free travel before tightening and connecting the chain.
4. Install a pinned LeRobot release using its current installation instructions. Identify ports and perform full-arm calibration for each role.
5. Run empty-gripper teleoperation slowly, confirm limits/directions, then add cameras and record a short dataset through the same software release.

**Expected checkpoint:** Correctly identified joints respond once, calibration persists, and leader–follower motion stays within the assembled mechanism's limits.

## Development software and recovery

Use the Seeed hardware tutorial with the upstream LeRobot SO-101 workflow. Command-line flags vary by release; check each command's --help. Archive software commit, servo firmware, IDs, role, gearing and calibration with the arm. Do not import SO-100 joint assumptions into the SO-101 structure.

## FAQs

**Is 114993667 a ready-to-use assembled pair?** No; verify the purchased BOM and provide the required mechanics and peripherals.

**Why do multiple servos respond together?** Default IDs may be duplicated. Disconnect the chain and follow the one-servo-at-a-time ID procedure.

## Sources and validation

* [Seeed Pro-edition hardware and complete workflow](https://wiki.seeedstudio.com/lerobot_so100m_new/)
* [Seeed product part-number catalog](https://files.seeedstudio.com/wiki/wiki-platform/2026_Seeed_Studio_Catalog.pdf)
* [LeRobot SO-101](https://huggingface.co/docs/lerobot/so101)
* [SO-101 mechanical repository](https://github.com/TheRobotStudio/SO-ARM100)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
