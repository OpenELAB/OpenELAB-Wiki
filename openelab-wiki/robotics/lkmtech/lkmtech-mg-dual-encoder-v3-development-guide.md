# LKMTECH MG Dual-Encoder V3 Actuator Engineering Guide

[TB-LKM-MG4010E-i36C](https://openelab.io/products/mg4010e-i36-v3-dual-encoder-robot-motor) · [TB-LKM-MG4005E-i10C](https://openelab.io/products/mg4005e-i10-v3-dual-encoder-robot-motor) · [TB-LKM-MG5010E-i10C](https://openelab.io/products/mg5010e-i10-v3-high-torque-dual-encoder-drive-motor)

### Product and scope

This page covers **MG4010E-i36 V3**, **MG4005E-i10 V3** and **MG5010E-i10 V3**. They share an integrated-actuator concept but have different gearing, drive limits and torque/speed ratings. CAN and RS485 variants must be identified from the supplied unit.

### Hardware and technical documents

| Item              | Reference                                                           |
| ----------------- | ------------------------------------------------------------------- |
| MG4010E-i36       | 36:1 family; not the i10 motor                                      |
| MG4005E-i10       | 10:1 compact joint                                                  |
| MG5010E-i10       | 10:1 larger joint                                                   |
| Nominal reference | 24V model family; driver operating range is model/revision-specific |
| Feedback          | E-series dual motor/output encoder configuration                    |

The linked **LK product catalogue** and model-specific **dimension/driver datasheets** are the technical starting points. Public sheets disagree on some speed, torque/current constants and driver voltage ranges. **Do not combine them into a single V3 rating.** Match the exact order/label to its signed-off parameter sheet before final sizing or powering.

### Getting started

1. Record the full model, CAN/RS485 option and driver revision. Select the corresponding manual and pinout.
2. Mount one unloaded motor, verify the confirmed supply rating and wire power/data with power off.
3. Use the matching LK motor configuration tool/interface to inspect identity, angle, temperature and errors.
4. Record communication settings and export parameters before changing IDs or zero position.
5. Only after revision/limits are confirmed, run a small low-speed test and verify stop behavior.

**Expected checkpoint:** valid status readings from the identified actuator. Numeric motion limits remain subject to exact revision confirmation where public sheets conflict.

### Development software and recovery

Use the exact LK protocol/tool package supplied with the motor. A public universal SDK/version was not established in this review; no speculative command bytes are provided. Preserve drive parameters, zero reference and protocol revision with application code.

### FAQs

**Can i10 scaling be reused for i36?** No; verify shaft units, gearing and model scaling.

**Does a second encoder remove backlash?** Feedback and mechanical backlash are separate properties.

**Which conflicting datasheet should be used?** Obtain the exact unit's manufacturer-approved parameter sheet before design sign-off.

### Sources and validation

* [LK product catalogue, manufacturer literature hosted by a supplier](https://makerselectronics.com/wp-content/uploads/2025/05/LK%E4%BA%A7%E5%93%81%E6%89%8B%E5%86%8C%EF%BC%88%E8%8B%B1%E6%96%87%EF%BC%8925.02.11-1-MG4.pdf)
* [MG4005E-i10 V3 dimensional/driver sheet hosted by Riotech](https://riotech.co.kr/wp-content/uploads/2024/10/MG4005E-i10-V3.pdf)
* [MG5010E-i10 V3 dimensional/driver sheet hosted by Riotech](https://riotech.co.kr/wp-content/uploads/2024/10/MG5010E-i10-V3.pdf)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
