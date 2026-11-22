# RealBot-S2: wheeled folding robot guide

{% hint style="info" %}
**Model: RealBot-S2, delivered RX75S arms.** This is a manufacturer-document reference. A current exact-model OpenELAB `.io` product/SKU match was not verified on 22 November 2026; no order link or substitute product is asserted. Check the delivered model, controller generation and project bill of materials before using technical procedures.
{% endhint %}

## Product overview

RealBot-S2 combines a four-wheel-steering, four-wheel-drive base, articulated folding body and two seven-axis RX75S arms. It is distinct from the older RMC-DA-LIII lifting platform and from the differential-drive RealBot-L2. The user manual is V1.0 dated 20 August 2026; the separate S2 API document is V1.3 dated 24 August 2026.

## Applications

Supervised teleoperation, robot data collection, perception development and mobile-manipulation research. Navigation, recording, remote access and particular cameras depend on the delivered project configuration; their appearance in a feature list does not make every interface public.

## Specifications

| Parameter                   | Value and scope                                                                         |
| --------------------------- | --------------------------------------------------------------------------------------- |
| Envelope / mass             | 614 × 552 × 1700 mm / approximately 125 kg                                              |
| Robot joints                | 20 DOF excluding chassis and end effectors: 14 arm + 4 body + 2 head                    |
| Arms                        | RX75S, 7 DOF and 5 kg rated payload per arm                                             |
| RX75S reach / repeatability | 691 mm / ±0.2 mm, per supplied S2 manual                                                |
| Battery                     | 48 V, 20 Ah; runtime approximately 6 h in the manual, dependent on operating conditions |
| Compute / OS                | Jetson AGX Orin 64 GB / Ubuntu 22.04                                                    |
| Body height change          | Articulated body motion; not the L2 independent lifting-column API                      |

Source: [S2 user manual V1.0, PDF pp. 8–12 \[S2\]](realman-source-library/); [S2 interface V1.3, PDF pp. 24–25 \[S2\_API\]](realman-source-library/). The S2 manual contains conflicting “lifting” figures (0.3 m versus 30 mm) and unclear translated chassis terminology. Do not use those lines as travel limits. Use the delivered kinematic model and S2 control appendix; the API document explicitly distinguishes the four body joints from an independent lift column.

## Hardware and connections

Identify the chassis LAN/debug port, WAN port, main power control, emergency stop and charging connections from PDF pp. 16–21. The manual describes two batteries: follow the actual delivery's battery and charger instructions; do not infer a pack connection from the system voltage. Keep the charging path, robot envelope and pinch zones clear.

The S2 arms are RX75S, with hard brakes on J1–J4 and soft wrist brakes on J5–J7 in the supplied manual. Support tools/loads during shutdown. Do not substitute standalone RX75 geometry or wire an accessory using the older platform's connector assumptions.

## Software and development resources

Use Ubuntu 22.04 / ROS 2 Humble and the **delivered S2 interface SDK**, whose `rm_robot_interfaces` messages match `/rm_app/rm_robot_ws/version.txt`. Public RM\_API2 and `ros2_rm_robot` are arm resources; installing them does not provide a complete supported S2 business interface. Do not launch a second hardware driver on the robot.

Start with [S2 development and interface boundaries](realbot-s2-development/). Continue to its read-only environment, telemetry and data-validation tutorials.

## Complete supplied document and engineering details

[RealBot-S2 user manual — all 38 PDF pages](realman-source-library/complete-s2-user-manual.md). The full reference is readable inside the wiki, with an original-page view and searchable text for every page. It includes the material not repeated in this entry guide.

| Source section                                                           | Full in-wiki reference                                                     |
| ------------------------------------------------------------------------ | -------------------------------------------------------------------------- |
| Cover, revision and original contents                                    | [PDF 1–5](realman-source-library/complete-s2-user-manual.md#pdf-page-1)    |
| Features, architecture, full-unit/arm/computer/camera specifications     | [PDF 6–15](realman-source-library/complete-s2-user-manual.md#pdf-page-6)   |
| Mechanical dimensions, controls, charging, emergency stop and interfaces | [PDF 16–18](realman-source-library/complete-s2-user-manual.md#pdf-page-16) |
| Local networking, SSH, Wi-Fi and wired networking                        | [PDF 19–22](realman-source-library/complete-s2-user-manual.md#pdf-page-19) |
| Android/desktop teach pendant and operating controls                     | [PDF 23–34](realman-source-library/complete-s2-user-manual.md#pdf-page-23) |
| Arm connection and six-axis force calibration                            | [PDF 35–36](realman-source-library/complete-s2-user-manual.md#pdf-page-35) |
| Safety, transport, storage, unpacking and further resources              | [PDF 36–38](realman-source-library/complete-s2-user-manual.md#pdf-page-36) |

### Complete platform setup and operation

The supplied user manual covers the full robot, arms, main controller and camera specifications separately. Its mechanical drawing and chassis-control/charging/debugging pages are part of the installation information, not optional illustrations. Record the delivered camera/computer/arm configuration before selecting an image, application or software profile.

The local-network chapter documents the chassis LAN connection and a `192.168.128.*` subnet, including access to `192.168.128.10`; the standalone-arm `192.168.1.18` procedure is a different context. The original Linux networking/SSH/Wi-Fi examples remain in the complete reader. Apply network changes only to the intended interface and keep an approved recovery path; do not replace working site networking with a copied factory profile. Factory credentials in the source describe that delivery, rather than a permanent credential policy.

The teach-pendant chapter includes Android installation and connection, desktop access, state model, camera view, packaging posture, initial posture, joint-angle controls, enabling, limits/error clearing, system status, real-time control and general configuration. These functions have different effects: seeing the state model is read-only; packaging, initialization, jogging, enabling and calibration may cause movement. Confirm control ownership and the attended stop arrangement before selecting an operating control.

The arm-programmer and force-calibration chapter includes the network prerequisites and the manufacturer's automatic calibration workflow. Calibration requires the delivered force-sensor/tool configuration and the required clear working envelope. A “Calibration Successful” message is a completion observation for that operation, not verification of arbitrary payload data or safe force-control limits.

### Chassis, power and service acceptance

| Area            | What the full source provides                                        | Acceptance evidence                                                        |
| --------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| Mechanics       | Complete-unit dimensions and chassis arrangement                     | Delivered dimensions, clearance, floor/path and cable routing              |
| Power           | Charging port, charging procedure and status                         | Correct charger and connection sequence for the supplied robot             |
| Safety          | Physical emergency stop, joint operation and maintenance precautions | Attended emergency-stop verification and recovery authority                |
| Network         | Local LAN, SSH, Wi-Fi, wired networking and external-IP discovery    | Actual addresses, interface names and a recoverable configuration          |
| Pendant         | Installation, connectivity, state/cameras, teaching and settings     | Matching app/controller release and a read-only status checkpoint          |
| Arm/force setup | Arm-programmer access and gravity/force calibration                  | Exact sensor/tool profile and recorded calibration result                  |
| Handling        | Transportation, storage and unpacking                                | Transport posture, packaging restraints, environment and inspection record |

For ROS 2 development, pair this operating manual with the separate complete S2 V1.3 interface reference. The hardware user manual does not define every topic, field, unit or control-authority rule.

Pair with [RealBot2.0 / S2 interface manual V1.3 — all 70 PDF pages](realman-source-library/complete-s2-interface-manual.md).

## Getting started

1. Record the robot serial, software version, hardware/camera profile and operating scene. Inspect damage, mounting, payload support, cables and emergency-stop locations with the trained operator.
2. Follow the delivered power-up procedure with control sources inactive and people clear of the full chassis, arm, head/body and pinch envelopes. Verify emergency-stop operation through the approved commissioning process before any motion test.
3. For the S2 manual's factory LAN setup, connect to the **LAN** port and use an unused host address in the delivered `192.168.128.*` subnet. The manual lists the robot host at `192.168.128.10`. Use project credentials and network configuration; do not change the robot's production DDS or internal arm addresses.
4. Access the robot's terminal using the authorized delivery account, read `cat /rm_app/rm_robot_ws/version.txt`, and follow the linked read-only ROS environment tutorial. Do not open the hardware-control page and press “execute” as a connectivity check.
5. Verify `/robot_slave/states`, `/diagnostics` and `/chassis/odom` with the delivered interface definitions and QoS. Check message freshness and physical subsystem health as well as topic presence.

**Expected result:** the correct version/profile is recorded and valid status/diagnostic data is readable without commanded motion. If any dependency is missing, keep the client in read-only mode. Sources: [S2 user manual V1.0, PDF pp. 19–24 \[S2\]](realman-source-library/); [S2 interface V1.3, PDF pp. 5–9, 17–24 \[S2\_API\]](realman-source-library/).

## Troubleshooting and FAQs

**Ping works but no ROS topics appear:** production DDS can be local-only. First inspect scene, ROS domain, RMW, SDK and whether external ROS access was delivered. Do not disable locality or firewall settings to force discovery.

**A collision topic never returns false:** S2 collision notifications are event-triggered. Latch the event in the client, stop non-zero commands, inspect on site and use the documented recovery sequence. Silence or a new command does not prove the hazard has cleared.

**Can I use the LIII or L2 lift controls?** No. Those platforms have different chassis/body mechanisms. Use the exact S2 body-joint contract and delivered limits; the user manual's translated lifting labels do not establish a standalone lift axis.

## Downloads and technical documents

| Resource                                                                           | Scope                                                         |
| ---------------------------------------------------------------------------------- | ------------------------------------------------------------- |
| [RealBot-S2 User Manual V1.0 \[S2\]](realman-source-library/)                      | Hardware, startup, network, teaching interface and handling   |
| [Secondary Development Interface V1.3 \[S2\_API\]](realman-source-library/)        | Public interfaces, QoS, units, validity, control and recovery |
| [S2 development hub](realbot-s2-development/)                                      | Version-bound entry point and tutorials                       |
| [Existing RMC-DA-LIII manual](embodied-double-arm-lifting-platform-user-manual.md) | Separate older platform; retained at its original URL         |

## References and validation

Source PDFs linked above, reviewed 22 November 2026. Software/hardware tests: **not run**. Source discrepancies and project-specific wiring, limits and camera profiles must be resolved against the delivery before powered or autonomous commissioning. This page provides a bounded status-reading path.
