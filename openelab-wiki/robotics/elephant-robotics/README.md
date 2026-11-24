---
description: >-
  Elephant Robotics manuals and myAGV Raspberry Pi 2023 development reference:
  exact image, serial SDK, ROS 1, calibration, mapping and navigation.
---

# Elephant Robotics

Elephant Robotics develops compact robots, end effectors, and learning platforms. Its desktop hardware is used for robot programming, vision-guided manipulation, and hands-on education, with accessories that extend the same arm into different tasks.

[Browse Elephant Robotics products on OpenELAB](https://openelab.io/collections/brands-elephant-robotics)

### Popular product guides

Products in the OpenELAB Top200 net-sales snapshot for 17 August–17 November 2026, ordered by their original sales rank. Shared model-family guides appear once; match the exact model, SKU and purchased option. This dated sales order is separate from manufacturer website-traffic ranking.

| Product guide                                                                               | Models / order codes |
| ------------------------------------------------------------------------------------------- | -------------------- |
| [Elephant Robotics myAGV 2023 Pi: image matching and navigation bring-up](myagv-2023-pi.md) | MyAGV-2023-PI        |

### Product range

* myCobot desktop robotic-arm platforms
* Grippers, suction tools, camera mounts, and arm accessories
* Educational and companion-robot products

### Product families and examples

| Product                  | Typical use                                      | Links                                                                                       |
| ------------------------ | ------------------------------------------------ | ------------------------------------------------------------------------------------------- |
| myCobot 280 Pi 2023      | Raspberry Pi-based desktop robot-arm development | [OpenELAB product](https://openelab.io/products/elephant-6-dof-mycobot-280-raspberry-pi)    |
| myCobot adaptive gripper | Adapting a robot arm to varied object shapes     | [OpenELAB product](https://openelab.io/products/elephant-robotics-mycobot-adaptivegripper)  |
| myCobot flexible gripper | Handling objects with a flexible gripper         | [OpenELAB product](https://openelab.io/products/elephant-robotics-mycobot-flexible-gripper) |
| Camera Flange 2.0        | Adding a camera to a compatible robot arm        | [OpenELAB product](https://openelab.io/products/elephant-robotics-cameraflange-2version)    |

### Popular applications

* Teach robot-arm programming and coordinate-based motion.
* Prototype camera-guided sorting and desktop pick-and-place.
* Compare gripper and suction approaches for small-object handling.

[Explore Robotics documentation](../robotics-wiki-home-page.md) · [OpenELAB Wiki home](../../)

### Development paths and commissioning references

[myAGV Raspberry Pi 2023](myagv-2023-pi.md) covers the Pi 4 / Ubuntu 20.04 / ROS 1 Noetic lane, hardware and power, serial protocol and Python SDK, myBlockly/myStudio/AGV\_UI, image/MCU versions, ROS configuration, mapping, navigation and recovery. It retains the documented test-mode exclusions, autonomous motor-test sequence and Cancel → stopped → Start → next-goal behavior. Do not substitute myAGV Plus, Jetson or a ROS 2 image solely because the product family name is similar. The historical SKU differs in case from the current store SKU and is flagged in the product-link audit.

Source review and applicable static checks are recorded separately from building software, flashing firmware, calibration or physical motion. Use each guide’s source and validation notes when planning a development session.
