# Hiwonder NexArm ROS Version Engineering Guide

[Hiwonder-21010737](https://openelab.de/products/hiwonder-nexarm-ros-robotic-arm)

### Product and scope

This guide covers the **NexArm ROS kit**, OpenELAB **21010737**, rather than the separate ESP32 starter version. Match the Jetson/Raspberry Pi host and purchased perception/AI options before selecting software.

### Hardware and technical documents

| Item            | Reference                                                           |
| --------------- | ------------------------------------------------------------------- |
| Product role    | Programmable arm platform for vision and robot-learning experiments |
| Host scope      | ROS kit with model-specific Jetson/Raspberry Pi options             |
| Other version   | ESP32 NexArm has its own firmware and setup                         |
| Resource access | Some system-image/source packages require the order number          |

Use the **ROS-version** hardware/assembly and Appendix resources for supply, servo map, mounting, dimensions and accessory wiring. The ESP32 starter manual's power and connection table is not sufficient to validate a ROS package.

### Getting started

1. Identify the actual host, arm controller, supplied power equipment and cameras. Secure the arm and clear its swept volume.
2. Obtain the matching factory image/materials from the official ROS Appendix. Hiwonder explicitly requests an order number for some downloads.
3. Boot the image and establish the manual's host connection.
4. Check joint identification/calibration and run a small, unloaded manual motion using the documented control interface.
5. Test the camera preview separately before grasping or VLA/policy deployment.

**Expected checkpoint:** recognized joints and a predictable small movement, with the correct host image documented.

### Development software and recovery

Use the official ROS-version source and development environment. A VLA demonstration also requires its supported model, compute and dataset configuration; arm communication alone does not provide that capability. Preserve firmware, image and calibration records before recovery or update.

### FAQs

**The ESP32 instructions show a different app?** Use the ROS-version manual for this kit.

**Where is the system image?** Follow the official Appendix's order-number access procedure; do not use an unrelated robot image.

**Motion or vision is inconsistent?** Validate joint calibration, camera identity and transforms before changing a trained policy.

### Sources and validation

* [Official ROS Appendix and downloads](https://wiki.hiwonder.com/projects/NexArm/en/ros-version/docs/Appendix.html)
* [ESP32 version for explicit comparison only](https://wiki.hiwonder.com/projects/NexArm/en/esp32-version/docs/1_Getting_Started_NexArm.html)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
