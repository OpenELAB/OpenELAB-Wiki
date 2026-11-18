# RobStride Debug Board and Power Board Integration Guide

[ROBSTRIDE-Debug](https://openelab.io/products/robstride04-qdd-120n-m-integrated-joint-motor-module) · [ROBSTRIDE-Power](https://openelab.io/products/robstride-power-supply-board)

### Product and scope

**ROBSTRIDE-Debug** is a debugging accessory, not a ROBSTRIDE04 motor. **ROBSTRIDE-Power** is a power-board accessory. The motor and accessory variants share store navigation but have different functions and electrical requirements.

### Hardware and technical documents

| Item          | Reference                                                                                |
| ------------- | ---------------------------------------------------------------------------------------- |
| Debug board   | Host-to-actuator setup/communication accessory; verify board revision and supported tool |
| Power board   | Power-distribution/integration accessory; not automatically an AC/DC supply              |
| Motor scope   | Motor power, current and CAN protocol remain model-specific                              |
| Documentation | Manufacturer powerBoard manual and STEP model are separate resources                     |

The store's variant/packing table explicitly identifies the Debug Board separately. The manufacturer repository lists **Power supply board instructions V1.3\_20251226**, a **POWER\_PCB\_V1.3\_1105 STEP**, and a newer Chinese **V1.5\_20260507** manual. Match the physical board; these revision labels are not interchangeable.

### Getting started

1. Identify the board and its connectors/revision before connecting a motor or external supply.
2. For the debug board, install the manufacturer-supported tool/driver and verify host enumeration.
3. Read the exact board and motor pinouts, then connect one secured, unloaded actuator with power off.
4. Use read-only identification/status first; the adapter's USB power is not a substitute for the motor supply.
5. For the power board, confirm input range, polarity, branch/fuse limits and any regeneration/discharge requirements before energizing.

**Expected checkpoint:** host/interface recognition and valid motor status, or a verified power-board installation against its exact manual.

### Development software and recovery

Use RobStride's current download/tool resources and the motor's matching protocol. A power-distribution board has no general application SDK. Save board/motor revision and wiring records. **Manual file availability was verified, but power-board PDF contents were not readable through this review environment**, so no unverified voltage/current rating is published.

### FAQs

**Does the Debug Board option include a motor?** The checked store listing says it contains the accessory only.

**Does Power Board mean power supply?** Confirm function; do not connect mains to an assumed DC distribution input.

**Can board V1.3 wiring be applied to V1.5?** Only after confirming the current manual and hardware.

### Sources and validation

* [Verified Debug Board variant identity](https://openelab.io/products/robstride04-qdd-120n-m-integrated-joint-motor-module)
* [Official English power-board manual/CAD folder](https://github.com/RobStride/Product_Information/tree/main/Product%20Literature/powerBoard)
* [Official current Chinese power-board resources](https://github.com/RobStride/Product_Information/tree/main/%E4%BA%A7%E5%93%81%E8%B5%84%E6%96%99/powerBoard)
* [Manufacturer download entry point](https://robstride.com/)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
