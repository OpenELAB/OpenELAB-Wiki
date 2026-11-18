# DAMIAO DM-J4310-2EC and DM-J8009P-2EC Engineering Guide

[DM-J4310-2EC-24V-V3](https://openelab.io/products/damiao-brushless-servo-dm-j4310) · [DM-J8009P-2EC-V3](https://openelab.io/products/damiao-brushless-servo-dm-j8009p)

### Product and scope

This guide distinguishes **DM-J4310-2EC** from **DM-J8009P-2EC**. OpenELAB's SKU suffix **V3** must be reconciled with the physical motor/driver revision; it is not proof that a manufacturer manual labeled V1.1 describes the same revision.

### Hardware and technical documents

| Item          | Reference                                                                |
| ------------- | ------------------------------------------------------------------------ |
| DM-J4310-2EC  | Compact dual-encoder geared joint; 10:1 family scope                     |
| DM-J8009P-2EC | Larger dual-encoder, cross-roller-bearing joint; 40Nm peak-class listing |
| Communication | Model/firmware-specific CAN control                                      |
| Feedback      | Motor/output encoder configuration must match the manual                 |
| Revision rule | Use the exact full model and hardware/firmware label                     |

The model manual index links separate **DM-J4310-2EC V1.1** and **DM-J8009P-2EC** documents, connector maps and control references. Confirm supply, current, torque scaling and mechanical drawings for the delivered revision before powering or designing a bracket.

### Getting started

1. Fixture one unloaded motor and record its model, voltage label, firmware and CAN IDs.
2. Connect the documented supply and compatible USB-CAN interface; check termination.
3. Use the supported DAMIAO debugging tool to read identity/status before changing parameters.
4. Select the exact model and control mode; retain its position, velocity and torque scaling.
5. Perform a small low-speed motion with conservative current/limits, then test stop/disable.

**Expected checkpoint:** correct identity/status and predictable motion using verified model scaling.

### Development software and recovery

Use the manufacturer's model-specific command protocol and the **dmBots motor-debugging-tool** workflow linked by Seeed's DM quick start. Do not mix MIT-style packed control with position/velocity modes or another motor's scaling. Back up parameters and zero/calibration data before firmware or ID changes.

### FAQs

**Does V3 automatically mean manual V1.1?** No; verify the physical/firmware revision.

**All joints respond together?** Check duplicate CAN IDs with one motor isolated at a time.

**Unexpected high speed or torque?** Disable immediately and inspect units, model limits, gearing and control-mode selection.

### Sources and validation

* [Model-specific English manual index](https://damiao.enactic.ai/en/)
* [Official application/tool route in Seeed DM guide](https://wiki.seeedstudio.com/rebot_b601_dm_getting_started/)
* [Debugging tool](https://github.com/dmBots/motor-debugging-tool)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
