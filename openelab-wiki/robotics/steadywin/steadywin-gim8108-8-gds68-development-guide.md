# SteadyWin GIM8108-8 GDS68 Dual-Encoder Engineering Guide

[SW-GIM8108-8-S68-2E](https://openelab.io/products/steadywin-gim8108-8-robot-motor)

### Product and scope

OpenELAB **SW-GIM8108-8-S68-2E** is the GIM8108-8 configuration with the corresponding **GDS68/secondary-encoder** scope. GDZ468 and GDK468 driver options have different communication and software requirements.

### Hardware and technical documents

| Item              | Reference                                                                       |
| ----------------- | ------------------------------------------------------------------------------- |
| Actuator          | GIM8108-8, 8:1 planetary reduction                                              |
| Driver scope      | GDS68 rather than GDZ/GDK                                                       |
| Communication     | Manufacturer identifies GDS68 as CAN                                            |
| PC setup path     | Manufacturer specifies Type-C for GDS68                                         |
| Secondary encoder | Retains single-turn position after power loss; does not remove gearbox backlash |

The manufacturer page links **GIM8108-8 2D PDF/STEP**, **GDS68 driver documents** and selection tables. Use the **GDS** data for supply, current and thermal limits; the product page's broad family range is not a substitute for the exact drive rating.

### Getting started

1. Identify the driver and secondary encoder from the physical label/options.
2. Fixture the unloaded motor and confirm its exact electrical limits and wiring.
3. Connect using the supported GDS68 PC setup method and read status/parameters.
4. Save the parameter set, IDs and zero reference.
5. Use the GDS68 manual's conservative small-motion test, then verify stop behavior and single-turn position retention as documented.

**Expected checkpoint:** valid GDS68 status and predictable bounded motion with a saved parameter baseline.

### Development software and recovery

Use the **GDS68** software/protocol package linked by SteadyWin. GDZ468's USB-RS485 tool path and Modbus support must not be assigned to GDS68. Some manufacturer driver documents are Chinese-only; retain the original protocol/units when translating.

### FAQs

**Does the secondary encoder eliminate backlash?** The manufacturer explicitly says it does not.

**Why does a GDZ tool not connect?** Match the driver and communication interface.

**Can I import another GIM ratio's settings?** Verify gearing, current, units and calibration rather than copying a parameter set.

### Sources and validation

* [Manufacturer exact product, options, CAD and GDS resources](https://steadywin-motor.com/products/planetary-reduction-motor-robot-dog-humanoid-robot-joint-module-flat-thin-large-torque)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
