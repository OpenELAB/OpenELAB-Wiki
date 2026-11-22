# RealBot-L2: platform and teleoperation reference

{% hint style="info" %}
**Model: RealBot-L2, project-defined configuration.** This is a manufacturer-document reference. A current exact-model OpenELAB `.io` product/SKU match was not verified on 22 November 2026; no order link or substitute product is asserted. Check the delivered model, controller generation and project bill of materials before using technical procedures.
{% endhint %}

### Product overview

The supplied V2+ solution white paper describes a wheeled dual-arm robot with a differential-drive base, an independent lifting column, one head-pitch axis and one waist-pitch axis. It is a solution/planning document, not an installation or interface-control manual. S2 uses a different chassis and body; the older RMC-DA-LIII is another separate platform.

### Applications

Supervised service-robot research, manipulation, teleoperation and demonstration-data collection. Human-friendly appearance, compliant control and obstacle-avoidance claims do not establish safety certification for operation around people or pets.

### Specifications

| Parameter         | Value and scope                                                                                                                     |
| ----------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| Height / mass     | 1.4–1.7 m / approximately 120 kg                                                                                                    |
| Base / drive      | 595 × 465 × 210 mm / dual-wheel differential                                                                                        |
| Lifting column    | 300 mm stroke; white-paper speed 50–100 mm/s; ≥60 kg column rating is not arm payload                                               |
| Arms              | Two 7-DOF arms; 5 kg per arm; approximately 690 mm horizontal reach excluding tools                                                 |
| Head / waist      | One pitch DOF each; distinct from the S2 two-head/four-body-joint API                                                               |
| Battery / runtime | 48 V, 20 Ah; >4 h active operation and approximately 1 h charge as white-paper estimates                                            |
| Gripper option    | 90 mm stroke, 30 N, ±0.02 mm in the white paper; not RMG22-65                                                                       |
| Compute options   | White paper alternates DEEPX S100 and RDK S100 wording; Jetson AGX Orin 64 GB is also listed. Confirm the exact delivered platform. |

Source: [L2 V2+ white paper, PDF pp. 2, 9–12 \[L2\]](realman-source-library.md). All white-paper figures remain subject to the signed technical agreement and delivery list. Do not convert advertised maximum speed, slope or obstacle figures into operating limits without commissioning evidence.

### Hardware and connections

Match the delivered base, arm pair, lift, quick-change tools, cameras, charger and stop controls. The white paper does not supply complete power pinouts, a charging interlock specification, lifting installation details or a verified stop circuit. Keep commissioning de-energized until the operating manual and drawings are available.

The wrist camera is described as Orbbec Gemini 335Lg. Camera count, mounts and calibration must match the delivery; do not transplant S2 camera topics or standalone RX75's D405 specification.

### Software and development resources

The white paper describes fourth-generation control, a teleoperation client and data pipeline, but provides no complete L2 ROS package/API contract. Obtain the versioned L2 SDK, supported host OS, message definitions, license and recovery guide from the delivery. The S2 V1.3 API expressly limits itself to S2 and is not a generic L2 SDK.

Two teleoperation options are distinct: the immersive workstation uses RX71 master arms; the Aloha-style exoskeleton kit uses a separate isomorphic servo-arm assembly and Ethernet conversion box. Stanford Mobile ALOHA concepts do not establish software or wiring compatibility with this supplied implementation. Source: [L2 V2+ white paper, PDF pp. 13–20 \[L2\]](realman-source-library.md).

### Getting started

1. Keep the system de-energized and compare the actual delivery list with white-paper §10: robot, end effectors, teleoperation workstation/license, optional Aloha kit, charger, spares and technical documents.
2. Record the compute module, arm model/handedness, quick-change tool, battery/charger labels and camera part numbers. Resolve the S100 naming conflict against physical labels and the signed bill of materials.
3. Obtain the L2 operating manual, dimensioned drawings, grounding/power and emergency-stop instructions, tool/lift load limits, network diagram, exact firmware/SDK and license terms.
4. Confirm which teleoperation option was supplied and obtain its own calibration, joint-direction, stop and recovery procedure. Do not enable a master-slave mapping based on a “1:1” marketing statement.
5. Agree a supervised commissioning plan with staged identity, status, stop and then one-axis motion acceptance. Keep the S2 `/robot/command` and `/cmd_vel` examples out of this plan unless an L2 delivery document explicitly supports them.

**Expected result:** a complete delivery/technical-document checklist and a clearly identified software/hardware configuration. This first result requires no energization or robot motion.

### Troubleshooting and FAQs

**Is the 60 kg lift rating the robot's handling payload?** No. It describes the lift mechanism in the white paper. Each arm is separately rated 5 kg, with tool/geometry and stability constraints still applicable.

**Which S100 board is supported?** The supplied white paper uses conflicting names. Verify the actual compute module and corresponding image/toolchain before ordering or installing software.

**Can I use RMG22-65 instructions?** Only if that exact gripper is delivered and its power/protocol match is confirmed. The white-paper 90 mm/30 N tool has different specifications.

### Downloads and technical documents

| Resource                                                                             | Purpose                                                               |
| ------------------------------------------------------------------------------------ | --------------------------------------------------------------------- |
| [RealBot-L2 Product Solution White Paper V2+ \[L2\]](realman-source-library.md)      | Architecture, options and planning specifications                     |
| [S2 comparison](realbot-s2-guide.md)                                                 | Distinguish folding-body/four-wheel system; not an L2 operating guide |
| [Older lifting-platform manual](embodied-double-arm-lifting-platform-user-manual.md) | Separate RMC-DA-LIII source, preserved for its installed base         |

The L2 installation manual, schematics, CAD, versioned SDK and firmware/recovery package were not part of these ten supplied files. Obtain the delivery-specific set before commissioning.

### References and validation

[L2 V2+ white paper, PDF pp. 2, 9–20, 24–26 \[L2\]](realman-source-library.md). Reviewed 22 November 2026. Software/hardware tests: **not run**. This is a source-backed planning reference; installation and operation remain blocked by the missing delivery-specific technical set.
