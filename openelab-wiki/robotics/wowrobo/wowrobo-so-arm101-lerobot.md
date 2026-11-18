# WowRobo SO-ARM101 leader–follower kit: identify, calibrate and teleoperate

{% hint style="info" %}
[**View WowRobo SO-ARM101 leader–follower kit: identify, calibrate and teleoperate on OpenELAB**](https://openelab.io/products/wowrobo-robotics-so-arm101-diy)

**Product model/family:** WowRobo SO-ARM101 leader–follower kit: identify, calibrate and teleoperate · **OpenELAB SKU:** `WR-ARM101-Kit`
{% endhint %}

[WR-ARM101-Kit](https://openelab.io/products/wowrobo-robotics-so-arm101-diy)

## Product and scope

The WR-ARM101-Kit is a leader–follower robot-learning platform for teleoperation, demonstration datasets and imitation learning with LeRobot. DIY and assembled versions differ in preparation. Treat the WowRobo kit BOM and power supplies as the authority for this kit; Seeed's Pro-edition voltage rules do not identify the WowRobo variant.

## Hardware and technical documents

| Item                     | Reference                                                                      |
| ------------------------ | ------------------------------------------------------------------------------ |
| Platform                 | SO-ARM101 leader and follower                                                  |
| Software                 | Hugging Face LeRobot; pin a documented release or commit                       |
| Mechanical design        | SO-101 revision of TheRobotStudio SO-ARM100 repository                         |
| Power and servo variants | Verify each arm's servo labels, gearing and supplied adapter before connection |

Inventory servos, controllers, brackets, printed parts, clamps, cables and supplies against the purchased option. The manufacturer offers DIY and assembled versions. The exact WR-Kit leader/follower voltage combination was not independently established in accessible documentation; confirm it from the supplied BOM or WowRobo before applying power. Secure both bases and provide an accessible power disconnect.

## Getting started

1. For a DIY kit, follow the SO-101 mechanical files and supplier assembly instructions. Configure one unconfigured servo at a time, using the correct voltage and target role/ID; do not connect a chain of duplicate default IDs.
2. Install the LeRobot environment from its installation guide. Record the release/commit and optional dependencies instead of mixing commands from different releases.
3. Find and record the two controller ports. Identify the physical leader and follower; use the current release's so101\_leader and so101\_follower configuration instructions.
4. Calibrate each assembled arm within its mechanical limits using the documented LeRobot workflow. Do not reset IDs on a working preconfigured kit.
5. Start low-speed teleoperation with an empty gripper and clear workspace. Record a short demonstration only after joint direction, limits and stopping behavior are correct.

**Expected checkpoint:** The follower tracks deliberate leader movements without hitting limits, with stable port identities and saved calibration.

## Development software and recovery

Use the LeRobot SO-101 guide for camera setup, dataset recording, replay and policy training. The repository supplies code; the robot CAD repository supplies mechanical files and BOM. Check each repository's license before distributing derivatives. Keep the calibration with the individual arm, not just with a shared workstation.

## FAQs

**The controller is visible but no servo responds.** Check the separately supplied servo power, connector seating and correct voltage; USB enumeration alone does not establish servo power.

**Can I reuse calibration from another arm?** Calibrate the actual physical assembly; horn indexing and joint offsets vary.

## Sources and validation

* [WowRobo manufacturer's kit](https://shop.wowrobo.com/products/so-arm101-diy-kit-assembled-version-1)
* [OpenELAB exact kit](https://openelab.io/products/wowrobo-robotics-so-arm101-diy)
* [LeRobot SO-101 workflow](https://huggingface.co/docs/lerobot/so101)
* [LeRobot installation](https://huggingface.co/docs/lerobot/installation)
* [SO-101 CAD and BOM](https://github.com/TheRobotStudio/SO-ARM100)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
