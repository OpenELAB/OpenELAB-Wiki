# RobStride 10P CAN and CAN-FD Engineering Guide

[ROBSTRIDE-10P](https://openelab.io/products/robstride-10p-qdd-joint-actuator)

### Product and scope

**ROBSTRIDE-10P** is an integrated robotic joint. The current manufacturer repository separates **CAN2.0 10P** and **RS10P-CANFD** documentation. Confirm the purchased protocol variant before choosing a parser, adapter or firmware.

### Hardware and technical documents

| Item                 | Reference                                                |
| -------------------- | -------------------------------------------------------- |
| Product scope        | 10P joint; not RS06                                      |
| Ordering description | 42Nm peak-class actuator; verify exact manual conditions |
| CAN2.0 manual        | RS10PUser Manual260907.pdf                               |
| CAN-FD manual        | RS10PCANFDUser Manual261016.pdf                          |
| CAD                  | RS10P-20261030 STEP model in the corresponding folder    |

The official repository contains **model-specific manual and STEP files**. Their existence and exact paths were verified; the PDF contents could not be fetched in this review. **Supply, pinout, current/torque limits and scaling must be checked in the matching manual before power or motion.** No RS00–RS06 parameter table is silently applied to 10P.

### Getting started

1. Identify CAN2.0 versus CAN-FD and obtain/read that manual.
2. Fixture one unloaded actuator and verify its electrical and connector requirements.
3. Connect a compatible interface and inspect identity/status with the supported setup tool.
4. Record firmware, bus settings and parameter limits before writes.
5. After confirming the exact control scaling, run a conservative small-motion and stop/disable test.

**Expected checkpoint:** valid identity/status from the correct protocol variant before enabling motion.

### Development software and recovery

The manufacturer maintains separate protocol-generation folders. A SocketCAN example for older RS00–RS06 is not evidence of 10P support. Preserve manual revision and firmware with the application. Use only the documented 10P update/recovery path.

### FAQs

**Can an RS06 configuration be reused?** No; gearing, limits and protocol scope differ.

**Does a CAN-FD adapter prove firmware compatibility?** The frame format and device firmware must also match.

**Why are some numeric fields absent?** The exact manual must be read before publishing unverified electrical or control limits.

### Sources and validation

* [Official CAN2.0 manual and CAD folder](https://github.com/RobStride/Product_Information/tree/main/Product%20Literature/CAN2.0/10P)
* [Official CAN-FD manual and CAD folder](https://github.com/RobStride/Product_Information/tree/main/Product%20Literature/CANFD/RS10P-CANFD)
* [Manufacturer resource repository](https://github.com/RobStride/Product_Information)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
