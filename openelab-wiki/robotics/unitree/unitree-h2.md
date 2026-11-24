---
description: >-
  Identify H2 and H2 EDU options, inspect documented ports and manual revisions,
  and validate offline SDK contracts while charging, stop behavior and firmware
  gaps remain explicit.
---

# Unitree H2 and H2 EDU: interfaces, manuals and SDK contract checks

{% hint style="info" %}
[**View Unitree H2 on OpenELAB**](https://openelab.io/products/unitree-h2-humanoid-robot-with) — SKU `Unitree-H2`\
[**View Unitree H2 EDU on OpenELAB**](https://openelab.io/products/unitree-h2-edu-humanoid-robot) — SKU `Unitree-H2-Edu`

**Model:** Unitree H2 / H2 EDU · **Scope:** 31-joint biped; optional hands and compute require the actual order configuration. H2-X and H2-D are separate platforms.
{% endhint %}

## Product overview <a href="#product-overview" id="product-overview"></a>

Unitree H2 is a full-size, approximately 70 kg humanoid with 31 body joints, binocular perception and voice interaction. This guide explains edition selection, the published H2 interfaces, manual-dependent commissioning and an offline SDK contract checkpoint. H2 EDU is the development edition in the manufacturer table; the base H2 column shows a slash for secondary development. A public example does not unlock a base robot. [H2 manufacturer specifications](https://www.unitree.com/H2/)

The English H2 User Manual V1.1, dated July 2, 2026 in its revision table, is the hardware reference here. Its emergency-stop description differs from the May 29 remote manual, and its battery information needs reconciliation with the battery/charger document. Physical commissioning remains a **source-bounded draft** until the delivered robot, battery, controller and firmware are matched to the correct instructions. The offline procedure below needs no robot power. [User manual, source page 39 / printed p.38](https://marketing.unitree.com/article/en/H2/User_Manual.html)

### Current H2 portal scope and H2Plus distinction <a href="#current-h2-portal-scope-and-h2plus-distinction" id="current-h2-portal-scope-and-h2plus-distinction"></a>

All **29 supplied H2 developer records** have now been reviewed, including empty categories, source examples and dedicated hand, audio, stereo, odometry and H2Plus GMSL chapters. They supplement the 60-page manual index retained below. An H2Plus camera/computer configuration is explicitly named in that collection; **no source establishes H2Plus as H2-X**. H2-X keeps its separate guide, ankle map, batteries and firmware gates. Exact delivered edition and component revisions still govern physical use. [H2 hardware](https://doc-cdn.unitree.com/25/1061/en/25_1061_en), [H2Plus GMSL scope](https://doc-cdn.unitree.com/25/1576/en/25_1576_en).

## Applications <a href="#applications" id="applications"></a>

* **Humanoid software research on H2 EDU:** body-state decoding, kinematic analysis and application integration, after verifying developer access and the delivered image. A 31-joint source example is a useful reference for state labeling, not a universal control program.
* **Supervised perception and interaction:** the binocular camera, microphone array and speaker support investigation of sensing and interaction. Camera calibration, stream API and time synchronization are still required for quantitative work.
* **Payload integration studies:** back mounting and power outputs are documented, but a carried sensor needs a separately checked mechanical design and electrical budget. The arm's advertised payload is not a back-mount rating.

These are engineering uses inferred from documented capabilities. No application certification or unattended operational reliability is established by the product page. Some demonstrated functions remain under development. [Manufacturer notes 1–7](https://www.unitree.com/H2/)

## Specifications <a href="#specifications" id="specifications"></a>

Both columns below describe the published H2 family, not every delivered optional configuration. Figures are manufacturer reported, not measured here. Torque maxima and payload figures depend on configuration and scenario. [Product table](https://www.unitree.com/H2/), [User Manual §3.4, source pages 8–9](https://marketing.unitree.com/article/en/H2/User_Manual.html)

| Parameter                           | H2                                                             | H2 EDU / engineering condition                                                                                                       |
| ----------------------------------- | -------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| Standing height × width × thickness | 1820 × 456 × 218 mm                                            | Same published dimensions                                                                                                            |
| Mass including battery              | About 70 kg                                                    | About 70 kg; verify added hardware                                                                                                   |
| Body joints                         | 31                                                             | 31; hands have their own configuration                                                                                               |
| Joint distribution                  | Each leg 6; each arm 7; waist 3; head 2                        | Same body distribution                                                                                                               |
| Dexterous hand                      | Slash in table                                                 | Multiple model options; not an included universal hand                                                                               |
| Maximum arm / leg joint torque      | 120 / 360 N·m                                                  | Same maxima; not continuous ratings                                                                                                  |
| Arm payload                         | Peak about 15 kg; rated about 7 kg                             | Same published values; posture and scenario matter                                                                                   |
| Calf + thigh / forearm + upper arm  | 1045 / 690 mm                                                  | Same published lengths                                                                                                               |
| Structure                           | Aircraft-grade aluminum, titanium alloy, engineering plastics  | Same material classes                                                                                                                |
| Motor / bearing / cooling           | Internal-rotor PMSM; crossed-roller bearing; local air cooling | No ingress rating implied                                                                                                            |
| Battery                             | 15 Ah, 0.972 kWh; maximum 75.6 V                               | Same family battery claim                                                                                                            |
| Compute                             | PC1 Intel Core i5                                              | PC1 i5 plus PC2 Intel Core i7 for custom development                                                                                 |
| Additional compute                  | Slash                                                          | Optional module choices, such as Thor; 2070 TOPS is not a standard CPU specification                                                 |
| Sensors / interaction               | Wide-FOV binocular camera; microphone array and speaker        | Exact calibration and interfaces need the delivered configuration                                                                    |
| Wireless / OTA                      | Wi-Fi 6, Bluetooth 5.2; OTA listed                             | OTA availability does not identify a validated firmware pair                                                                         |
| Runtime                             | About 3 h                                                      | Workload dependent; not a guaranteed walking endurance                                                                               |
| Speed                               | Product table says maximum speed ≥2 m/s                        | Manual printed p.31 separately mentions 3 m/s under specific configurations with practical limits; neither is a commissioning target |
| Development                         | Slash                                                          | YES; exact SDK and firmware still require matching                                                                                   |
| Accessories listed                  | Quick-release battery, charger, manual controller              | Manual accessory inventory additionally includes protective stand and calibration/packing fixtures; verify shipment                  |
| Warranty reference                  | 8 months                                                       | 12 months; actual regional sale terms govern                                                                                         |

The battery manual gives a nominal battery voltage of 64.8 V and charge limit of 75.6 V. Its charger table prints **76.5 V**, 2–6.6 A and 498.96 W. That discrepancy is visible in the original image. Do not select a charger by these numbers alone or silently correct them. Obtain the exact approved charger part number/nameplate and Unitree's resolution before charging. [Battery manual source pages 3–4 / printed pp.5–6](https://marketing.unitree.com/article/en/H2/Battery_Charger.html)

### H2 portal joint-limit reference <a href="#h2-portal-joint-limit-reference" id="h2-portal-joint-limit-reference"></a>

The following numerical intervals are source-reference radians for the illustrated full body. They are not approved combined targets, actuator-space AB limits or a collision-free motion envelope. Optional axes require actual configuration matching; do not infer physical joints from missing/padded transport slots. [Original joint reference](https://doc-cdn.unitree.com/25/1117/en/25_1117_en).

| Source ID | Exact source joint identifier | Reference interval, rad         |
| --------- | ----------------------------- | ------------------------------- |
| `0`       | `left_hip_pitch_joint`        | -2.4525975 to 2.7754225         |
| `1`       | `left_hip_roll_joint`         | -0.467441 to 2.1688605          |
| `2`       | `left_hip_yaw_joint`          | -2.827 to 2.827                 |
| `3`       | `left_knee_joint`             | -0.08725 to 2.53025             |
| `4`       | `left_ankle_roll_joint`       | -0.3490658503 to 0.296705972783 |
| `5`       | `left_ankle_pitch_joint`      | -1.13446401358 to 0.61086523808 |
| `6`       | `right_hip_pitch_joint`       | -2.4525975 to 2.7754225         |
| `7`       | `right_hip_roll_joint`        | -2.1688605 to 0.467441          |
| `8`       | `right_hip_yaw_joint`         | -2.827 to 2.827                 |
| `9`       | `right_knee_joint`            | -0.08725 to 2.53025             |
| `10`      | `right_ankle_roll_joint`      | -0.296705972783 to 0.3490658503 |
| `11`      | `right_ankle_pitch_joint`     | -1.13446401358 to 0.61086523808 |
| `12`      | `waist_yaw_joint`             | -1.7453 to 1.7453               |
| `13`      | `waist_A_joint`               | -0.5236 to 0.5236               |
| `14`      | `waist_B_joint`               | -0.43633 to 0.5236              |
| `15`      | `left_shoulder_pitch_joint`   | -2.6179939 to 1.8325957         |
| `16`      | `left_shoulder_roll_joint`    | -0.517 to 2.494                 |
| `17`      | `left_shoulder_yaw_joint`     | -2.6179939 to 2.6179939         |
| `18`      | `left_elbow_joint`            | -0.986111 to 3.0717795          |
| `19`      | `left_wrist_roll_joint`       | -2.6179939 to 2.6179939         |
| `20`      | `left_wrist_pitch_joint`      | -0.576 to 0.576                 |
| `21`      | `left_wrist_yaw_joint`        | -1.2217305 to 1.2217305         |
| `22`      | `right_shoulder_pitch_joint`  | -2.6179939 to 1.8325957         |
| `23`      | `right_shoulder_roll_joint`   | -2.494 to 0.517                 |
| `24`      | `right_shoulder_yaw_joint`    | -2.6179939 to 2.6179939         |
| `25`      | `right_elbow_joint`           | -0.986111 to 3.0717795          |
| `26`      | `right_wrist_roll_joint`      | -2.6179939 to 2.6179939         |
| `27`      | `right_wrist_pitch_joint`     | -0.576 to 0.576                 |
| `28`      | `right_wrist_yaw_joint`       | -1.2217305 to 1.2217305         |
| `29`      | `head_pitch_joint`            | -0.5236 to 0.83775              |
| `30`      | `head_yaw_joint`              | -1.7453 to 1.7453               |

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

### Identify the installed interfaces before connecting anything <a href="#identify-the-installed-interfaces-before-connecting-anything" id="identify-the-installed-interfaces-before-connecting-anything"></a>

H2 User Manual §3.5 uses a **top view**, not the view into a loose mating cable. Read the port map and front/back connector drawings together. The illustrations below are manufacturer diagrams; do not mirror them or infer wire colors. The same connector shape may carry different voltages and buses. [Port map, source page 10 / printed p.9](https://marketing.unitree.com/article/en/H2/User_Manual.html)

| H2 port                      | Published role                                                                         | Integration consequence                                                                              |
| ---------------------------- | -------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| \[1], GXT30(2)-M             | Direct battery output plus RS-485 to PC2                                               | 54–75.6 V, rated 10 A per p.11; not a regulated 54 V supply                                          |
| \[2] and \[11]               | 24 V / 10 A plus CAN to PC2                                                            | Verify number and mating orientation; not interchangeable with \[1]                                  |
| \[10]                        | 12 V / 10 A plus RS-485 to PC2                                                         | A 24 V load cannot be assumed compatible                                                             |
| \[3] Type-C                  | USB 3.0 host, DP 1.4, PD 3.0 to PC2                                                    | PD profile is not specified in this table                                                            |
| \[4], \[5] Type-C            | USB host / 5 V 2 A in default routing; optional PC3/PC4 changes role and may add DP/PD | Record installed compute before choosing a cable/display                                             |
| \[6] GMSL                    | Optional video input to PC3                                                            | Not a generic USB camera connector                                                                   |
| \[7], \[8], \[9] Type-C      | USB 3.0 host / 5 V 2 A; \[8]/\[9] route according to optional PC3/PC4                  | Physical symmetry does not prove host routing                                                        |
| \[12], \[15] RJ45            | Gigabit Ethernet on 192.168.123.x / 192.168.124.x respectively                         | These are documented subnet families, not a verified host IP, mask, DDS interface or PoE power input |
| \[13], \[14] hand connectors | Standard 24 V / 10 A, RS-485 and USB 2.0; optional 100 Mbps Ethernet variant           | Verify the installed hand-interface version before connecting a hand                                 |

Total external output power **excluding the direct battery output must not exceed 500 W**. In the RS-485/USB hand configuration, \[10] and \[13] share a bus; \[1] and \[14] share a bus. These are shared-bus constraints, not four independent serial channels. Supply voltages above are not logic-level ratings. No cable fabrication is authorized by this summary. [§3.5 source pages 10–12 / printed pp.9–11](https://marketing.unitree.com/article/en/H2/User_Manual.html)

[Original H2 connector orientation and pinout figure, source page 12](https://doc-cdn.unitree.com/static/2026/7/3/b69a5c188c444438b0f6f5152476325b_2482x3509.png). The drawing itself prints `458_B` at one hand connector; preserve that source ambiguity rather than designing a harness from a corrected guess. Connector assignments, CAN/RS-485 electrical characteristics, termination and optional routing must be confirmed against the actual unit before peripheral power is enabled.

Back mounting dimensions appear in §3.3, source page 7 / printed p.6, with M6 threaded holes and depth callouts. Use the original drawing for orientation and screw engagement; no permissible accessory mass or tightening torque is established here. [Original manual](https://marketing.unitree.com/article/en/H2/User_Manual.html)

### Power, suspension and stop conditions <a href="#power-suspension-and-stop-conditions" id="power-suspension-and-stop-conditions"></a>

The H2 manual requires dry, non-dusty conditions at **0–40°C**, an open flat area, visual supervision and at least 2 m clearance from people/obstacles. It explicitly says H2 is not waterproof or dustproof. These whole-robot limits take precedence over a wider standalone battery temperature range. Suspend the robot using its designated shoulder latches and protective stand with locked casters; the pre-start pose affects upper-limb and ankle zero positions. Do not free-stand an unqualified unit to investigate software. [§5.1–5.4, source pages 15–19](https://marketing.unitree.com/article/en/H2/User_Manual.html)

Charging chapters specify the genuine pack, powered off and removed from the robot, allowed to cool to room temperature, with supervised charging on a noncombustible surface. General charging sections say AC first then battery, but shipping-mode activation text reverses that order and specifies 220 V. The charger table says 100–240 V AC, 50/60 Hz. Resolve that sequence and the voltage discrepancy with the actual approved pack/charger instructions before energizing; do not derive an external DC input from the battery-output table. [User §4, source pages 13–14; battery §§1,7,9](https://marketing.unitree.com/article/en/H2/Battery_Charger.html)

**Stop behavior is revision dependent.** User Manual §5.6 says a hard remote stop removes joint power and the robot can fall directly; Remote Manual §13 says the controller attempts to squat and enters zero torque if it has not squatted within 1.5 s. Both require restart; the remote describes a three-second button lockout and solid versus flashing link indicators. Do not promise a controlled squat, braking hold or a remote stop during low-level development. The user manual warns remote commands fail during low-level development and may conflict with high-level commands. Confirm the current firmware/controller stop contract and mechanical protection before any live session. [User source pages 4,26–27](https://marketing.unitree.com/article/en/H2/User_Manual.html), [Remote source pages 5,10](https://marketing.unitree.com/article/en/H2/Remote_Control.html)

### H2 L2+B timing and mode discrepancies <a href="#h2-l2b-timing-and-mode-discrepancies" id="h2-l2b-timing-and-mode-discrepancies"></a>

The same button label is described differently across these source contexts. The rows are a comparison of published behavior, **not a combined operating sequence**.

| Exact source / context                                                                                                                                                                  | Published L2+B wording and resulting mode                                                                                                            | Qualification boundary                                                                                       |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| User Manual V1.1 §5.4, [source page 20](https://doc-cdn.unitree.com/static/2026/7/3/8bf2263d96874be493051792510804d1_2481x3508.png) (printed p.19), post-startup emergency-stop summary | Simply describes pressing L2+B to enter damping and lower toward the ground; no hold duration is stated here.                                        | This shorter wording does not establish that a brief press implements the timed soft stop below.             |
| User Manual V1.1 §5.6, [source page 26](https://doc-cdn.unitree.com/static/2026/7/3/9565c2ad421747ce810fea1bce0fa733_2481x3508.png) (printed p.25), soft emergency stop                 | Explicitly describes holding L2+B for **more than 5 seconds**, followed by a damped state and descent toward the ground.                             | Do not omit the stated duration or turn the description into a guaranteed stable hold.                       |
| User Manual V1.1 §5.8, [source page 28](https://doc-cdn.unitree.com/static/2026/7/3/90cbc283b29d49ae97a2a6e744543636_2482x3508.png) (printed p.27), suspended/debugging context         | Describes an L2+B press entering damping and a **second L2+B press entering zero-torque mode**.                                                      | The repeated-button transition is specific to this debugging description; it is not a universal stop toggle. |
| R3 Remote Manual V1.0 §12, [source page 9](https://doc-cdn.unitree.com/static/2026/6/3/cd2ec12baedf448186785881977e77c7_2481x3508.png), mode chart and motion-control note              | Chart pairs a long L2 press with a B click for damping; the note separately describes a 5-second hold for damping protection in motion-control mode. | This chart/note does not resolve the user manual's different timing and mode contexts.                       |

Resolve the delivered firmware, active mode, remote revision/overlay and exact support instructions before live use. Damping, descent and zero torque must not be treated as a braking hold; support can be lost and the robot can fall. The source differences remain unresolved here, and none of these button actions forms part of the offline first result.

### Portal electrical routing and the shared peripheral budget <a href="#portal-electrical-routing-and-the-shared-peripheral-budget" id="portal-electrical-routing-and-the-shared-peripheral-budget"></a>

The [numbered rear-interface figure](https://doc-cdn.unitree.com/static/2026/1/23/1f2d5c85696742fc941a1ea93f6486a8_2698x1749.png) and connector figures have been visually checked. The current H2 article supplies routing missing from a connector photograph alone:

| Port       | Electrical/interface role                                           | Routing and qualification                                                      |
| ---------- | ------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| `1`        | `VBAT+485`, 54–75.6 V, 10 A                                         | Direct battery output plus RS-485 to PC2; not regulated 24 V or a charge input |
| `2`, `11`  | 24 V / 10 A plus CAN                                                | PC2                                                                            |
| `10`       | 12 V / 10 A plus RS-485                                             | PC2                                                                            |
| `3`        | Type-C USB3, DP1.4, PD3.0                                           | PC2                                                                            |
| `4`, `5`   | USB3 / 5 V 2 A without optional PC; full USB/DP/PD with optional PC | `4` routes to PC3 when fitted; `5` to PC4; otherwise PC2                       |
| `7`        | USB3 / 5 V 2 A                                                      | PC2                                                                            |
| `8`, `9`   | USB3 / 5 V 2 A                                                      | PC2 normally; `8` to PC3 / `9` to PC4 when fitted                              |
| `6`        | GMSL input                                                          | PC3 only, requires that optional computer/configuration                        |
| `12`, `15` | Gigabit Ethernet                                                    | `.123.x` / `.124.x`, respectively                                              |
| `13`, `14` | Standard hand board: 24 V / 10 A, RS-485, USB2                      | RS-485 to PC2, USB2 to PC1; optional board provides 100 Mbps Ethernet instead  |

**All regulated external outputs together are limited to 500 W; the direct VBAT output is excluded from that stated regulated-output budget.** A per-port 10 A label does not permit every output to supply 10 A simultaneously. RS-485 is shared between `10` and `13`, and between `1` and `14`; account for bus ownership/addresses rather than assuming independent buses. The existing **75.6 V battery/76.5 V charger-manual discrepancy remains unresolved**; a peripheral-output table does not resolve a charger setting or make another power package compatible. [About H2](https://doc-cdn.unitree.com/25/1061/en/25_1061_en).

The [GXT30 polarity/signal figure](https://doc-cdn.unitree.com/static/2026/10/9/caa3c05c11004c73a23210b463d79e4c_806x275.png) shows **different polarity orientations**: in its panel view, left-side `1/2` have power `−` then `+`, while right-side `10/11` have `+` then `−`. Signal labels also reverse: `1` RS485 A/B, `2` CAN H/L, `10` RS485 B/A, `11` CAN L/H. Preserve the original viewing orientation; this is not an inferred mating-cable contact numbering. Do not wire by left/right symmetry. [Assembly and wiring source](https://doc-cdn.unitree.com/25/1553/en/25_1553_en).

The [hand connector front/back figure](https://doc-cdn.unitree.com/static/2026/10/9/7c29b7557a8346b99a0bb6b4503ba4e3_707x398.png) labels front power between `458_B(TX/N)` and `USB_DP(RX/P)`, and rear ground between `USB_DN(RX/N)` and `485_A(TX/P)`. `458_B` is the drawing's apparent typo, retained here rather than silently changing an identifier. The combined labels cover different board/protocol options; they do not authorize simultaneous USB, Ethernet and RS-485 on an unmatched harness. Match actual board, side, signal function and approved cable before connecting unpowered hardware.

### Computers, addresses and sensor configurations <a href="#computers-addresses-and-sensor-configurations" id="computers-addresses-and-sensor-configurations"></a>

| Role         | H2 portal hardware reference                                                                   | Address / ownership                                         |
| ------------ | ---------------------------------------------------------------------------------------------- | ----------------------------------------------------------- |
| PC1          | Core i5 platform computer                                                                      | Reserved official motion/services; not external development |
| PC2          | Core i7, 10 cores / 12 threads, up to 4.70/4.80 GHz, 16/32 GB LPDDR5-5200, ≥500 GB             | `.123.162` / `.124.162`, developer computer                 |
| Optional PC3 | Thor T5000, 14-core Arm Neoverse-V3AE, 128 GB LPDDR5X, 273 GB/s, 2 TB NVMe, 40–130 W reference | `.123.163` / `.124.163`                                     |
| Optional PC4 | Orin NX 16 GB, eight-core Cortex-A78AE, 102.4 GB/s, 2 TB NVMe, 10–25 W reference               | `.123.164` / `.124.164`                                     |

PC3's **2070 TFLOPS is FP4-sparse**, not a directly comparable generic TOPS number or measured application rate. Module power/codec/graphics claims are reference capabilities, not guaranteed installed software. The current About chapter gives PC2 initial user `unitree`, password `Unitree0408`, early images `Unitree#24226`; Quick Development instead gives `123`, and the copied architecture paragraph calls a G1 developer computer `.164`. These are explicit source/image conflicts. Use the actual delivered image and approved access record; no login was attempted, and the `.161` ping/control endpoint is not PC2 SSH. [About](https://doc-cdn.unitree.com/25/1061/en/25_1061_en), [quick development](https://doc-cdn.unitree.com/25/1107/en/25_1107_en), [architecture](https://doc-cdn.unitree.com/25/1106/en/25_1106_en).

The H2/H2 EDU reference head camera is PC1/MIPI four-lane, two global-shutter sensors, 2064×1552 RAW12 at 30 FPS, 60 mm baseline, H/V FOV 156°/116°, F2.0, focal length 1.53 mm and −20–60°C camera environment. The H2Plus reference is PC3/GMSL, 2560×1984 RAW10 at 30 FPS, baseline 60±0.5 mm, FOV 140±3°/102±3°, F2.0, 2.67 mm and −30–70°C. Sensor operating temperature does not enlarge whole-robot environmental limits; raw sensor size is not a transmitted-stream contract. Neither row applies to H2-X by name similarity.

The back panel is curved. The [original mounting reference](https://doc-cdn.unitree.com/static/2026/6/5/145f3085d6f14d8cb808d8d88afdf6cd_322x285.png) points to the exact 3D model for actual hole positions; bracket load, screw engagement and torque still require matching engineering data. Do not flatten the image into a universal mounting template.

### H2 hand installation and compatible routing choices <a href="#h2-hand-installation-and-compatible-routing-choices" id="h2-hand-installation-and-compatible-routing-choices"></a>

The dedicated assembly chapter starts with four wrist fixings for the original rubber hand and uses **H2-specific adapters and covers**. Side-exit Dex3 routing differs from end-exit Dex5: the latter requires the matching front structure/Mylar and cable path, followed by the correct covers. Marked sleeves/clamps retain the harness along the arm; avoid pinching or placing tension through wrist travel. These are service/assembly operations on isolated, supported hardware, not an instruction to disassemble a powered robot. The source does not specify all fastener torques or structural load ratings. [Assembly chapter](https://doc-cdn.unitree.com/25/1553/en/25_1553_en), [original clamp/routing figure](https://doc-cdn.unitree.com/static/2026/8/18/38637e6f26e04c2bb835cf566efbecd5_1326x645.png).

| Adapted hand family in the source                      | Power / communications contract                                                                                                                  |
| ------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| Dex1-1                                                 | 24 V, RS-485 to PC2                                                                                                                              |
| Dex3-1 standard/tactile, Dex5-1 / Dex5-1P              | 24 V, USB to PC1, matching DDS software                                                                                                          |
| BrainCo Revo2 basic/tactile, Revo3 U21B / U21T / U21 V | 24 V, RS-485 to PC2                                                                                                                              |
| Inspire DFQ                                            | 24 V, RS-485 to PC2                                                                                                                              |
| Inspire E2                                             | 24 V, matching 100 Mbps Ethernet hand-board option                                                                                               |
| Wujihand2                                              | **12 V from port `10`, not 24 V from `13/14`**, with Ethernet on the matching `13/14` board                                                      |
| Sharpa                                                 | 24 V hand power plus **Gigabit Ethernet at `12/15`**; this consumes a debug/network port, with compatible Type-C expansion considered separately |

The source lists fourteen adaptation kits across these variants. A listed kit is not an included robot option, a new robot SKU or permission to substitute another vendor's pinout. Match side, adapter, board, cable and installed driver before choosing a protocol. The budget, shared-bus and polarity limits above still apply.

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

The source baseline is **Unitree SDK2 C++ commit `b7fec6020eb93d4c059a6edf19905e12a75a8d3d`**. Its README lists Ubuntu 20.04 LTS, aarch64/x86\_64 and GCC 9.4.0; its build instructions require CMake, Make, yaml-cpp, Eigen, Boost and fmt. These are source/prebuilt environment facts, not the verified OS or firmware on an H2 EDU. SDK installation, compilation and network execution have not been performed. [Pinned README](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/README.md)

| Contract / resource              | What was established                                                                          | Limit                                                                                                                                                              |
| -------------------------------- | --------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| H2 low-level ankle example       | `unitree_hg::msg::dds_::LowState_`; `rt/lowstate`; `rt/secondary_imu`; 31 active body indices | Also publishes `rt/lowcmd` and changes controller ownership; do not run for a first read                                                                           |
| HG IDL                           | `motor_state` has 35 transport slots; `tick`, `mode_machine`, IMU and CRC fields exist        | 35 slots do not mean 35 physical H2 joints; units and active mappings need model evidence                                                                          |
| H2 termination example           | Subscriber only; orientation and missing-message warnings                                     | Not an emergency-stop controller; shares state across callback/main thread without an explicit snapshot lock and checks orientation before a verified first sample |
| H2 locomotion API                | `sport` service, API version `1.0.0.0`; getters 7001–7008 with 7006 deprecated                | Source API version does not establish delivered firmware support                                                                                                   |
| H2 arm action / arm SDK examples | Separate arm API and DDS examples exist                                                       | Arm actions and arm enabling are control operations, not a state prerequisite                                                                                      |

The [H2 source joint map](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/h2/low_level/h2_ankle_swing_example.cpp) labels left ankle **roll 4 / pitch 5**, right ankle **roll 10 / pitch 11**, waist 12–14, left arm 15–21, right arm 22–28 and head 29–30. H2-X reverses the ankle pitch/roll ordering at those indices. Match the actual firmware map before labeling telemetry; never copy H2-X gains or output commands into H2 because both have 31 joints.

The [H2 locomotion header](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/h2/loco/h2_loco_client.hpp) only writes getter output parameters after a zero return code. `GetFsmId`, `GetFsmMode`, `GetBalanceMode`, `GetSwingHeight`, `GetStandHeight`, `GetArmSdkStatus` and `GetAvailableFsmIds` are distinct from setters. `StopMove`, `Damp`, `ZeroTorque` and `ReleaseMode`-style ownership operations are **not read-only**. No RPC is needed for the offline checkpoint.

The H2 arm-action header names service `arm`, API version `1.0.0.14`: execute preset action 7106, get action list 7107, execute custom action 7108 and stop custom action 7113. `GetActionList` is distinct from executing an action. The client’s built-in action-name map is explicitly a local list, not a response queried from the robot; it cannot prove a particular firmware supports a gesture. [Pinned arm API and client](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/h2/arm/h2_arm_action_client.hpp)

The separate arm DDS demo publishes HG commands on `rt/arm_sdk`, uses upper-body indices 15–30, and treats command slot **31 as an arm-SDK weight**, not an extra body joint or hand actuator. Its source accepts FSM 4 or 703, enables arm SDK control, then performs staged arm/head motion at a 20 ms nominal control interval. These are source conditions, not permission or a verified firmware contract. The locomotion command example also prints getter outputs without checking each return code; it is unsuitable as an authoritative first status probe. The H2 CMake file includes H2-D mobile targets alongside H2; those targets do not share biped applicability. [Arm DDS example](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/h2/high_level/h2_arm_sdk_dds_example.cpp), [locomotion example](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/h2/high_level/h2_loco_client_example.cpp)

The manual's debug chapter says the built-in motion controller sends zero-velocity commands even with no remote input. Entering a low-level development mode therefore requires the exact model's supported ownership procedure, suspension and stop plan; this page does not turn a debug key sequence into permission to actuate. Calibration §5.9 points to a separate video, and the manual says the factory-calibrated robot should not be recalibrated routinely. Neither that video nor an exact delivered firmware compatibility matrix was read in this guide. [User §5.8–5.9, source pages 28–29; §6 source page 32](https://marketing.unitree.com/article/en/H2/User_Manual.html)

### H2 message layout and high-level version boundaries <a href="#h2-message-layout-and-high-level-version-boundaries" id="h2-message-layout-and-high-level-version-boundaries"></a>

The H2 portal confirms HG `LowState_` / `LowCmd_`, thirty-one body indices inside **35 transport slots**, `mode_pr=0` PR or `1` direct AB for the coupled joints, millisecond `tick`, `w,x,y,z` quaternion and XYZ gyro/acceleration. Joint `q`, `dq`, `ddq` and estimated torque use rad, rad/s, rad/s² and N·m. Two temperatures, terminal voltage, sensors and fault words have their own generated field types. A physical-joint count does not identify unused command slots or a hand protocol. [Joint order](https://doc-cdn.unitree.com/25/1117/en/25_1117_en), [basic services](https://doc-cdn.unitree.com/25/1132/en/25_1132_en).

**Do not copy the portal's composite IDL sketch into a decoder.** It shows `MotorCmd.reserve[3]` and GO-like `q_raw/dq_raw/ddq_raw` motor fields that disagree with the pinned HG generated definitions (`MotorCmd` has one reserved element; the HG motor state does not have those raw fields). The received version/mode and exact generated schema must match the installed firmware. HG state has no embedded GO BMS structure; battery/mainboard feedback uses separate documented channels. Portal `rt/lf` captions and a copied odometry type label do not establish measured rates or the correct decoder. [Pinned HG definitions](https://github.com/unitreerobotics/unitree_sdk2/tree/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/hg).

The dedicated H2 RPC chapter adds query APIs **`7007` arm-SDK status / `7008` available FSM IDs** and active **`7108` punch / `7109` arm-SDK enable**. A table calls arm enabling temporarily unavailable while later text offers it; require delivered service support. A getter's output is usable only after a successful return. The sample's `std::map` processes keys lexically rather than preserving command-line order, and empty values can make front/back indexing invalid. It is a source example, not a reliable action sequencer or passive first result. [RPC routine](https://doc-cdn.unitree.com/25/1120/en/25_1120_en).

The H2 locomotion chapter assigns zero torque `0`, damp `1`, stand-up `4`, start `601`, and a source-specific motion transition **`703` before `ai_sport 2.5.4.11` / `701` afterward**. Stand/lie FSM `802/803` requires **`ai_sport ≥2.5.4.88` for those features**. These are feature/version relationships, not universal minimum H2 firmware. The pinned default `Move` duration is one second; explicit continuous movement uses a very long source duration. `BalanceStand` stops stepping, while `ContinuousGait` can continue stepping at zero requested velocity. `StopMove` requests zero velocity; it does not cut power or prove supported standstill. [H2 sport service](https://doc-cdn.unitree.com/25/1133/en/25_1133_en).

The H2 `rt/arm_sdk` route uses **slot `31.q` as blending weight 0–1**. Arms are `15–28`, head `29–30`, waist `12–14`; the portal table that calls `15–28` waist is wrong. Preserve the actual pinned enum and topic context. This weight is not physical joint 31, nor G1's slot-29 or H1's slot-9 blending convention. The exact H2 ankle order above remains roll `4/10`, pitch `5/11`; do not import H2-X or H1-2 ankle labeling.

### DDS/RPC transport, architecture and host preparation <a href="#ddsrpc-transport-architecture-and-host-preparation" id="ddsrpc-transport-architecture-and-host-preparation"></a>

H2's DDS chapter is largely reused common material. The actual pinned factory takes **two** domain/interface arguments, despite the portal's extra shared-memory argument; the subscriber uses receive-channel creation, despite a send-creator typo; `GetServerApiVersion` returns a string by value at this pin. Callback queues can decouple slow work but introduce buffered age. Last-data time is monotonic microseconds, not wall time; RPC `SetTimeout(float)` uses seconds, and lease acquisition can block. Default timeout and example loop periods are source constants, not physical timing guarantees. [DDS chapter](https://doc-cdn.unitree.com/25/1123/en/25_1123_en), [pinned factory](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/channel/channel_factory.hpp), [pinned client](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/client/client.hpp).

The architecture describes user-authorized cloud connectivity: BLE setup/authentication, HTTP account binding, MQTT monitoring/OTA/signaling, WebRTC media/state/control, and STUN/TURN peer connectivity/relay. These manufacturer descriptions are not an independent privacy/security audit. Continuous DDS state and request/response APIs have different failure/completion meanings. The SDK Overview's older “GST unsupported” statement conflicts with the newer actual media chapters; treat this as service/revision scope rather than declaring all streaming impossible. [Architecture](https://doc-cdn.unitree.com/25/1106/en/25_1106_en), [SDK overview](https://doc-cdn.unitree.com/25/1105/en/25_1105_en).

Quick Development recommends Ubuntu 20.04/22.04, with ROS optional. SDK2 does not need ROS just to use its native DDS wrapper. Resolve the actual checkout, globally installed library and generated binary location together; an old global library can override the source version intended by a new checkout. Its low-level example moves ankles/wrists after ownership handover and is not a state-availability test. Generic HelloWorld DDS publishing/close-reopen and ROS Foxy/Humble/CycloneDDS 0.10.2 examples teach transport; copied Go2 package names and topic screenshots are not H2/H2-X support evidence. Keep future simulator and live robot discovery isolated by the approved domain/interface configuration. [Quick development](https://doc-cdn.unitree.com/25/1107/en/25_1107_en), [ROS routine](https://doc-cdn.unitree.com/25/1130/en/25_1130_en), [DDS teaching example](https://doc-cdn.unitree.com/25/1131/en/25_1131_en).

### Odometry frame, clock and service prerequisites <a href="#odometry-frame-clock-and-service-prerequisites" id="odometry-frame-clock-and-service-prerequisites"></a>

The H2 odometry feature requires the built-in motion controller and **StateEstimator ≥2.1.0.12 for this service**; it is unavailable in Develop mode. The dedicated chapter names GO **`SportModeState_`**, not the `IMUState_` label in the copied common topic table. It reports `rt/odommodestate` at 500 Hz and `rt/lf/odommodestate` at 20 Hz as vendor service claims, not observed rates here. [Odometry](https://doc-cdn.unitree.com/25/1121/en/25_1121_en).

Position is metres and velocity m/s in the world frame. At initialization the world origin is the base's ground projection, +X forward, +Y left, +Z up; orientation uses quaternion `w,x,y,z`, RPY radians and yaw speed rad/s. Preserve the actual initialization/reset history and frame transforms before fusing with camera/LiDAR or a map. A device timestamp, DDS arrival and local monotonic receive age do not automatically share a clock. The example's indefinite callbacks/printing are not the bounded first state result.

### Audio, speech and multimedia interfaces <a href="#audio-speech-and-multimedia-interfaces" id="audio-speech-and-multimedia-interfaces"></a>

H2's voice chapter specifies an 8 Ω speaker, 10 W nominal/12 W peak, and four near-linear microphones at 30 mm spacing. It requires **`vui_service ≥2.3.0.1`, `vui ≥2.0.0.3` for these features** and explicitly reuses `g1::AudioClient`. The namespace does not transfer G1 audio hardware. TTS role `0` is Chinese, `1` English, without mixed-language requests. Volume is 0–100; LED channels are 0–255. `PlayStream(app_name,stream_id,pcm_data)` accepts mono 16 kHz, 16-bit PCM; same stream ID continues cached playback, a new ID interrupts. `PlayStop(app_name)` stops that application's audio, not robot motion. [Voice/audio service](https://doc-cdn.unitree.com/25/1126/en/25_1126_en).

`rt/audio_msg` uses `std_msgs::msg::dds_::String_` JSON: `index`, `timestamp`, `text`, `angle` 0–180, `speaker_id`, `sense`, `confidence`, `language`, `is_final`, or playback `play_state` 0 stopped / 1 playing. Non-streaming offline ASR is default and some semantic fields remain developing. The sample JSON has a missing comma/type inconsistency, so validate the actual message instead of copying it as a schema. Enabled/awake microphone PCM is multicast at **`239.168.123.161:5555`**, nominally 32000 bytes/s for the stated format; this does not establish synchronized timestamps. The example changes volume to 100, speaks, lights LEDs and records, so it is not a passive check.

The separate multimedia chapter explicitly reuses Go2 `VideoClient::GetImageSample` for a JPEG 720P request/response path, while its GStreamer route receives H.264 RTP multicast **`230.1.1.1:1720`, 1280×720 at 15 Hz**. This is not the stereo-port family below. Check codec/backend availability and actual capture success; legacy OpenCV 4.1.1/CUDA instructions are an example baseline, not a universal modern prerequisite. Source demos can write image files and loop indefinitely. [Multimedia service](https://doc-cdn.unitree.com/25/1443/en/25_1443_en).

### PC1 stereo streams and depth interpretation <a href="#pc1-stereo-streams-and-depth-interpretation" id="pc1-stereo-streams-and-depth-interpretation"></a>

The stereo chapter requires disabling conflicting `video_hub`, then manually starting **Stereo Patch PC1**, which is not auto-started by default. The destination defaults to `.123.170`; the web page at **`.123.161:9080`** or its `/set?ip=...` URL changes the receiving host, then the streaming service is restarted. That GET-looking configuration URL is a **write**, not a passive connectivity query. [Stereo acquisition](https://doc-cdn.unitree.com/25/1265/en/25_1265_en).

| Stream                         | Source transport and format                                                     |
| ------------------------------ | ------------------------------------------------------------------------------- |
| Stereo source RGB, unrectified | UDP `5002`, RTP H.264 payload 96 / 90 kHz, 1920×1080 at 15 FPS                  |
| Left RGB                       | UDP `5004`, H.264 RTP, 544×448 at 10 FPS                                        |
| Right RGB                      | UDP `5006`, H.264 RTP, 544×448 at 10 FPS                                        |
| Depth                          | Matching `unitree-dep-img` receiver creates `/dev/video-dep`, 544×448 at 10 FPS |

The linked receiver dependencies include `unitree-dep-img 1.0.0`, **amd64** v4l-utils 1.22.1 and an Ubuntu22.04-specific v4l2loopback package. Match host architecture/kernel/distribution; these are not an Orin ARM installation guarantee. The broad source firewall-disable command is not a default prerequisite; use the approved receiving interface and required ports. No packages or streams were run.

The source-only depth viewer reads 16-bit samples, ignores 0/65535 and divides by 1000 for displayed metres. It can save raw/color frames and change color maps; its appearance is not metric calibration. Source inspection also shows a **cached last frame can be returned after a failed read**, so a visible image alone is not evidence of fresh acquisition. Negotiate the actual V4L2 format/size/endian contract, check complete frame length and record real acquisition/receive timing. A raw depth number, percentile color normalization and synchronized RGB/depth alignment are different concepts. [Original reference viewer archive](https://oss-global-cdn.unitree.com/static/eedfb0b8067448f3999cfbb3b19bf15e.zip).

### H2Plus / optional Thor GMSL and calibration boundaries <a href="#h2plus-optional-thor-gmsl-and-calibration-boundaries" id="h2plus-optional-thor-gmsl-and-calibration-boundaries"></a>

The GMSL chapter distinguishes H2 EDU with **optional PC3 Thor and external wrist GMSL/network head**, from **H2Plus with PC3 standard and internal GMSL head**. It does not identify H2-X. JetPack7.0 and 7.1 use different driver/module/I²C initialization paths after reboot; driver/ISP installation changes the system and is excluded from this guide's first result. The linked Feishu driver folder returned a document shell in source collection; actual driver-package contents were not obtained or executed. Do not infer successful access from HTTP200. [GMSL chapter](https://doc-cdn.unitree.com/25/1576/en/25_1576_en).

The source identifies head S56 CAM0/1, wrist SHF3L and example `/dev/video2`/`3` paths; enumerate the delivered devices before assigning names. Its reference capture is 1920×1080 at 30 FPS. The JetPack7.1 arm64 calibration package reads per-module EEPROM data, but its utility also changes the I²C link-mux register: it is **not a hardware-neutral offline read**. Failure to obtain calibration requires matching model/JetPack/power/link diagnosis, not copying sample numbers or flashing an unqualified driver.

Calibration uses `fx,fy,cx,cy` in pixels, fisheye coefficients `k1..k4`, 3×3 `K`, rotation `R` from CAM0 to CAM1 and translation `T` in **millimetres**. These are camera-to-camera extrinsics, not a camera-to-robot-base TF. Factory calibration at 2560×1984 must be correctly scaled/cropped for 1920×1080 processing. The sample FOV≈130° is not a universal replacement for the hardware table's≈140° value, and sample matrices are not this reader's unit calibration. Changing a module requires its own calibration data.

## Getting started <a href="#getting-started" id="getting-started"></a>

### Prerequisites and model qualification <a href="#prerequisites-and-model-qualification" id="prerequisites-and-model-qualification"></a>

Keep H2 disconnected for this first result. A browser is sufficient for source inspection; Python 3 is optional for the synthetic log example below. For any later live state session, first establish the exact H2 EDU serial/order, body/hand options, controller revision, firmware/image, approved battery/charger, compatible development manual, per-unit network settings and qualified operator. Missing or conflicting information keeps the task offline.

### First working result: inspect the exact published H2 contracts <a href="#first-working-result-inspect-the-exact-published-h2-contracts" id="first-working-result-inspect-the-exact-published-h2-contracts"></a>

1. Open the [H2 ankle example at commit b7fec602](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/h2/low_level/h2_ankle_swing_example.cpp). Find `H2_NUM_MOTOR` and `H2JointIndex`. Record 31 body motors, left ankle roll 4 / pitch 5 and right ankle roll 10 / pitch 11. Read the file as text; do not run it.
2. Open the [H2-X ankle enum at the same commit](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/h2x/low_level/h2x_ankle_swing_example.cpp). Compare pitch 4 / roll 5 and pitch 10 / roll 11. This is an explicit model difference, not a suggested replacement map.
3. Open [HG LowState\_.hpp at the same commit](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/hg/LowState_.hpp). Find `motor_state_` and its 35-slot array. Record transport capacity separately from H2's 31 active body joints.
4. Open the [H2 termination example](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/h2/low_level/terminations.cpp). Find the `ChannelSubscriber<LowState_>` on `rt/lowstate`. Contrast this with the ankle example's command publisher. Identify why the termination program's warnings do not themselves stop a robot.

**Expected result:** a source-inspection note stating “H2: 31 body joints; HG: 35 slots; ankle roll/pitch 4/5 and 10/11; H2-X order differs; termination source subscribes only.” This is a useful model/schema distinction. It is not a connection test or firmware compatibility approval.

If a link is unavailable, source inspection is incomplete. Use the exact pinned file when access returns rather than another model or an unpinned branch. Do not infer compatibility from a similar filename.

### Self-contained synthetic log check <a href="#self-contained-synthetic-log-check" id="self-contained-synthetic-log-check"></a>

Copy the complete Python example below into a new file named `telemetry_log_check.py`, then run `python3 telemetry_log_check.py` with Python 3. It uses only the standard library and the data included in the example. The example needs no SDK, configuration file or robot/network connection.

```python
import math


def inspect_sample(sample, now_ms, previous_tick=None):
    # Synthetic receive times in one monotonic clock domain; not wall-clock time.
    if sample is None:
        return "REJECT missing sample"
    received = sample.get("received_ms")
    tick = sample.get("tick")
    values = sample.get("values")
    if type(received) not in (int, float) or not math.isfinite(received):
        return "REJECT invalid receive time"
    age_ms = now_ms - received
    if age_ms < 0 or age_ms > 1000:
        return "REJECT stale or future sample"
    if type(tick) is not int or not 0 <= tick < 2**32:
        return "REJECT invalid tick"
    if not isinstance(values, list) or not values or not all(
        type(v) in (int, float) and math.isfinite(v) for v in values
    ):
        return "REJECT invalid values"
    if previous_tick is not None:
        delta = (tick - previous_tick) % 2**32
        if not 0 < delta < 2**31:
            return "REJECT repeated or backward tick"
        return "ACCEPT advancing tick"
    return "ACCEPT first sample"


sample = {"received_ms": 1500, "tick": 11, "values": [0.1, -0.2]}
cases = [
    (None, None, "REJECT missing sample"),
    (sample, None, "ACCEPT first sample"),
    (sample, 10, "ACCEPT advancing tick"),
    (sample, 11, "REJECT repeated or backward tick"),
    ({**sample, "received_ms": 999}, 10, "REJECT stale or future sample"),
    ({**sample, "values": [float("nan")]}, 10, "REJECT invalid values"),
    ({**sample, "tick": 0}, 2**32 - 1, "ACCEPT advancing tick"),
]
for data, previous, expected in cases:
    result = inspect_sample(data, now_ms=2000, previous_tick=previous)
    if result != expected:
        raise RuntimeError((result, expected))
    print(result)
print("PASS: 7 synthetic cases; no robot connection")
```

**Expected result:** the seven acceptance/rejection lines below, followed by the PASS line. The first accepted sample has no previous tick; later samples must advance. The last case exercises unsigned 32-bit wrap. The code checks finite values and receive-time age separately from tick progression.

```
REJECT missing sample
ACCEPT first sample
ACCEPT advancing tick
REJECT repeated or backward tick
REJECT stale or future sample
REJECT invalid values
ACCEPT advancing tick
PASS: 7 synthetic cases; no robot connection
```

The two example values are arbitrary synthetic numbers, **not a robot joint layout or packet schema**. The 1000 ms window and unsigned 32-bit tick rule demonstrate diagnostic logic only; they are not certified safety limits or an assumption about every robot's telemetry. Real logs require the documented model-specific timestamp, rollover, session/restart and unit conventions. A controller restart must reset or requalify the previous-tick baseline. These cases are independent tests, not one continuous measured stream.

**If this check fails:** confirm that the entire example was copied, run it with Python 3, and compare the error/result with the expected lines. A stale/repeated/nonfinite sample must remain rejected; do not remove those checks to obtain PASS. Passing this example proves only that this synthetic logic behaves as shown.

### Later read-only checkpoint, after qualification <a href="#later-read-only-checkpoint-after-qualification" id="later-read-only-checkpoint-after-qualification"></a>

A qualified reader should use the exact documented state type/topic/interface/domain, synchronized snapshots, a first-valid-sample gate and advancing ticks with recent monotonic receive timestamps. Preserve model/revision and sample age with the record. Avoid publishers, motion demos, mode changes, calibration, OTA and ownership release. End data collection if state is absent, stale, nonfinite or inconsistent; the qualified operator handles the robot using the verified physical procedure. This live checkpoint has not been executed.

### Versioned remote controls and ownership boundaries <a href="#versioned-remote-controls-and-ownership-boundaries" id="versioned-remote-controls-and-ownership-boundaries"></a>

The portal's original controller charts were visually inspected. They identify **full-package versions1.0.2.6 and 1.0.3.1**, not universal minimum firmware. Both distinguish ordinary damping selection from a **motion-state L2+B hold of five seconds**. That delay does not establish an instantaneous independent emergency stop. The original manual's stop/damping descriptions and gravity/support limitations remain visible above; resolve actual controller/version and active control owner before physical operation. [Remote guide](https://doc-cdn.unitree.com/25/1103/en/25_1103_en).

In the1.0.3.1 chart, `L2+Y` selects zero torque, `L2+B` damping, `L2+UP` ready, `L2+X` lie/stand and `L1+UP/DOWN` held2 s the box posture route; `R2+A` held2 s enters running, `R1+Y` regular mode and `R1+B` held2 s dance mode. `START` toggles stepping/standing. Dance stop uses double `START`; interaction stop uses double `DOWN`, with gesture/dance availability depending on the selected mode. The older chart has different regular-mode/selection keys. These are **active** operations, including changes of posture or displacement, and are not prerequisites for a subscriber. Use the exact original chart and measured clear workspace for any separately qualified demonstration; none is a hardware-stop certification.

The developer specification says the built-in controller auto-starts and can keep issuing zero-velocity commands even with neutral sticks. A low-level publisher can therefore conflict with it. The protected stand's four castors must be secured, and the source's `L2+A` diagnostic **moves joints**. Neither neutral appearance, a diagnostic pose nor a host-program exit proves released ownership or an effective low-level escape. The existing conditional state-only workflow intentionally makes no ownership change. [Developer specification](https://doc-cdn.unitree.com/25/1260/en/25_1260_en).

The remote payload uses 40 bytes: two-byte header,16-bit buttons, floats `lx,rx,ry,L2,ly`,16idle bytes. Bit order is `R1,L1,start,select,R2,L2,F1,F2,A,B,X,Y,up,right,down,left`; sticks span−1..1. The copied conversion example uses a GO type although H2 body state is HG. Decode the actual HG remote-byte field with matching packing/endian/header/finite checks; do not change the whole state decoder to fit the copied example. [Remote data](https://doc-cdn.unitree.com/25/1119/en/25_1119_en).

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

**Battery will not turn on outside the robot.** The battery manual describes load detection: it cannot turn on unless inserted in the robot and turns off when removed. Shipping mode can also prevent startup. Do not bridge contacts or add an improvised external cable. Resolve the exact pack/charger activation procedure first. [Battery §§1,4,8](https://marketing.unitree.com/article/en/H2/Battery_Charger.html)

**Head does not initialize after about two minutes.** The H2 manual treats no head movement during suspended startup as failed initialization. Recheck suspension, startup pose, battery condition and pre-start inventory; preserve fault information for [Unitree technical support](https://global-serviceconsole.unitree.com/#/work-order). Repeated free-standing retries or immediate recalibration are not supported recovery. [User §6, source pages 31–32](https://marketing.unitree.com/article/en/H2/User_Manual.html)

**Explore cannot find or bind H2.** The manual calls for an enterprise account, phone Bluetooth and app Bluetooth permission. Check the exact robot identity and existing account binding before changing network mode. AP and router modes are separate workflows; do not assume the illustrative hotspot credentials or H1-labeled screenshots are H2 defaults. Read-only inspection does not require pressing GO or unbinding an account. [User §5.5, source pages 20–24](https://marketing.unitree.com/article/en/H2/User_Manual.html)

**DL is lit but emergency-stop status flashes.** The remote manual distinguishes the data link from the emergency-stop link; flashing stop status means its stop unit is not connected. Do not interpret DL alone as a verified stop. Keep the robot mechanically protected and resolve controller/firmware matching. [Remote §§9,11,13](https://marketing.unitree.com/article/en/H2/Remote_Control.html)

**Telemetry has 35 slots or ankle names look wrong.** Compare HG message capacity with the 31-joint H2 enum and check H2 versus H2-X identity. Do not infer four additional active motors or reuse the other model's map. [Pinned H2 example](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/h2/low_level/h2_ankle_swing_example.cpp)

**Robot shakes when custom control starts.** The manual describes conflicts with its built-in controller. End the development attempt using the qualified operator's model-specific procedure. Diagnose edition, ownership and firmware before another attempt; the offline checker cannot approve takeover. [User §5.8](https://marketing.unitree.com/article/en/H2/User_Manual.html)

**Maintenance or storage is due.** With power off, check damage, battery latch/interface, cooling paths, remote controls and foot condition. The manual's foot-airbag procedure identifies two bolts to loosen but not remove; use its figure rather than a text-only reconstruction. The battery document recommends checking stored charge and recharging from below 30% to 70%, and gives disposal/transport instructions; these are not permission to deliberately run a robot to a depleted state. Consult the actual shipment/transport requirements. [User §8, source pages 33–36](https://marketing.unitree.com/article/en/H2/User_Manual.html), [Battery §9, source pages 9–11](https://marketing.unitree.com/article/en/H2/Battery_Charger.html)

### API, fault and media diagnostics added by the portal <a href="#api-fault-and-media-diagnostics-added-by-the-portal" id="api-fault-and-media-diagnostics-added-by-the-portal"></a>

Separate transport/API failures from robot faults. RPC `3001` is unknown; `3102..3107` mean send failure, unregistered API, timeout, request/response mismatch, invalid response and invalid lease. Server `3201` is response-send failure and is not returned to the client; `3202..3207` mean internal error, unimplemented API, bad parameters, rejected request, invalid lease and existing lease. Record versions/request identity instead of automatically retrying an uncertain physical action. [DDS/RPC reference](https://doc-cdn.unitree.com/25/1123/en/25_1123_en).

Motor faults are bitmasks in the exact HG family definition: voltage/current, chip/MOS/shell/winding temperature, encoders, BOOT/reset/authentication/calibration and communication/driver/version checks are distinct. The high directional timeout bits `0x40000000`/`0x80000000` do not replace lower fault bits. Retain raw source/motor/family, mode, tick and local receive age; do not clear a fault by reflashing or substitute GO raw-motor fields to make numbers look plausible. An HG state sample does not establish pack health or absence of a physical stop trigger. [Basic service/fault fields](https://doc-cdn.unitree.com/25/1132/en/25_1132_en).

For absent video, distinguish missing service/version from the wrong destination, codec, receiving interface, negotiated frame size and backend support. Do not disable the motion controller or system firewall as a generic media repair. For inconsistent depth, distinguish invalid samples, stale cached frames, wrong dimensions/endian handling, calibration resolution and RGB/depth timing before claiming distance accuracy. For GMSL, preserve module identity and JetPack/calibration provenance; the EEPROM utility's I²C writes and driver changes require their own qualified procedure.

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

| Resource                             | Purpose / exact scope                                                                                           | Link                                                                                                                                                 |
| ------------------------------------ | --------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| H2 User Manual V1.1                  | July 2, 2026; 39 source images, printed pp.2–38 plus front matter; H2/H2 EDU                                    | [Official English article](https://marketing.unitree.com/article/en/H2/User_Manual.html)                                                             |
| H2 Emergency Stop Remote Manual V1.0 | May 29, 2026; 10 source images; R3 remote and stop linkage                                                      | [Official English article](https://marketing.unitree.com/article/en/H2/Remote_Control.html)                                                          |
| H2 Battery and Charger V1.1          | June 17, 2026; 11 source images; voltage/activation discrepancies retained                                      | [Official English article](https://marketing.unitree.com/article/en/H2/Battery_Charger.html)                                                         |
| Complete chapter and figure index    | Original engineering interpretation and individual official page-image links for all 60 H2 manual source images | [H2 manual coverage and source-page index](unitree-h2.md#h2-manual-chapter-and-source-page-appendix)                                                 |
| Explore app download                 | Manufacturer's H2 entry; app/install alone does not confer an enterprise account                                | [Unitree Explore for H2](https://www.unitree.com/app/H2/)                                                                                            |
| H2 state and control source          | Pinned SDK2; source inspection only                                                                             | [H2 example directory](https://github.com/unitreerobotics/unitree_sdk2/tree/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/h2)                     |
| State schema                         | HG transport fields and 35 slots                                                                                | [LowState\_.hpp](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/hg/LowState_.hpp) |
| Developer document center            | Further manuals/videos must be read for the exact purchased revision                                            | [Official support portal](https://support.unitree.com/main/en)                                                                                       |

A standalone full electrical schematic, camera calibration package, exact compatible firmware release and delivered-unit API matrix were not verified. The public article is an image-based reader; no PDF download is invented. Manual artwork remains at Unitree's original URLs. See also the separate [H2-X manufacturer specifications](https://www.unitree.com/H2-X/) and [G1+ manufacturer specifications](https://www.unitree.com/G1pl/) for explicit non-interchangeability.

### H2 manual chapter and source-page appendix <a href="#h2-manual-chapter-and-source-page-appendix" id="h2-manual-chapter-and-source-page-appendix"></a>

This index retains all 39 user-manual, 10 remote-manual and 11 battery-manual source-page references. Summaries are original engineering interpretation, not manual reproductions or exact transcripts. The numbered links open Unitree's original page images. Source page means the one-based image sequence in each article; printed numbering differs, particularly in the battery manual. Confirm the exact original diagram before connector, button-glyph or servicing decisions. All physical conditions and unresolved revision differences in this guide still apply.

#### Chapter map and engineering decisions <a href="#chapter-map-and-engineering-decisions" id="chapter-map-and-engineering-decisions"></a>

| Document / chapter               | Source pages | What the H2 guide retains                                                                        |
| -------------------------------- | ------------ | ------------------------------------------------------------------------------------------------ |
| User front matter, §§1–2         | 1–4          | Identity, responsibilities, safe distance, command conflict and remote limitations               |
| User §3.1–3.4                    | 5–9          | Accessories, body/mount drawing, base/EDU specs and development rights                           |
| User §3.5                        | 10–12        | Port numbering, compute routing, power budget and original pinout orientation                    |
| User §4                          | 13–14        | Charging/cooling requirements; unresolved pack/charger activation conflicts                      |
| User §5.1–5.4                    | 15–19        | Environment, unboxing, pre-start checks, suspension and startup-dependent zero positions         |
| User §5.5–5.7                    | 20–27        | App/binding/network flow, remote/stop behavior and status colors; no blind UI/credential copying |
| User §5.8–5.11                   | 28–30        | Debug ownership, calibration-video gap, supported shutdown and packing                           |
| User §§6–8                       | 31–36        | Fault/recovery checks, factory-calibration caution, maintenance and foot-airbag figure           |
| User §9 / regulatory / revisions | 36–39        | Warranty distinction and original notices; exact V1.1 date                                       |
| Remote §§1–4                     | 1–3          | R3 parts, electrical/interface specs and joystick assembly                                       |
| Remote §§5–9                     | 4–5          | Calibration, power, feedback and independent emergency-stop link                                 |
| Remote §§10–12                   | 6–9          | Charging, binding, joystick/mode/interaction chart; glyph/firmware condition                     |
| Remote §§13–14                   | 10           | Stop behavior conflicts with user manual; V1.0 revision date                                     |
| Battery §§1–3                    | 1–4          | Identity, pack/charger dimensions and voltage conflict                                           |
| Battery §§4–8                    | 4–8          | BMS functions, state-specific LEDs, button timing, charge order and fault recovery               |
| Battery §§9–10                   | 9–11         | Use/charge/storage/transport/disposal and V1.1 revision                                          |

The index covers these three manual revisions; it does not replace the original diagrams or referenced videos/developer instructions. Resolve charger/activation, emergency-stop, timing and firmware discrepancies before commissioning. For maintenance and connector work, follow the exact original figure and qualified model-specific instructions.

#### H2 User Manual V1.1 <a href="#h2-user-manual-v11" id="h2-user-manual-v11"></a>

[Official image-based article](https://marketing.unitree.com/article/en/H2/User_Manual.html). No PDF URL is inferred.

| Source page | Original engineering interpretation / figure purpose                                                                                                               | Original source image                                                                                          |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------- |
| 1           | Cover identifies H2 User Manual V1.1; applicability is H2, not H2-X.                                                                                               | [Unitree image 1](https://doc-cdn.unitree.com/static/2026/7/3/213164bdc25344d8abee1155c5011f22_2481x3509.png)  |
| 2           | Contents locates overview, charging, use, maintenance, warranty, radio notices and revision history.                                                               | [Unitree image 2](https://doc-cdn.unitree.com/static/2026/7/3/313424d7fcd24eef9888fbc80dae2268_2481x3509.png)  |
| 3           | Disclaimer describes responsibility and service scope; no additional commercial or technical guarantee is inferred.                                                | [Unitree image 3](https://doc-cdn.unitree.com/static/2026/7/3/15a683a89992443699f6e25f76ddd22c_2481x3509.png)  |
| 4           | Disclaimer continues; safety section distinguishes high-level command conflicts from loss of remote commands during low-level development.                         | [Unitree image 4](https://doc-cdn.unitree.com/static/2026/7/3/d9424518dad149cd8b8244cfad740eda_2481x3509.png)  |
| 5           | Introduction and accessory inventory: full-size 31-joint platform, optional Thor compute and protective stand; check actual shipment.                              | [Unitree image 5](https://doc-cdn.unitree.com/static/2026/7/3/5ecd0446e48b416891e55ea44b1f8632_2482x3509.png)  |
| 6           | Accessory inventory continues with calibration fixtures, lanyard, foot airbags, tools and connectors; possession does not authorize calibration.                   | [Unitree image 6](https://doc-cdn.unitree.com/static/2026/7/3/f039322a98e84e14b66eb4a7396938cc_2482x3509.png)  |
| 7           | Body parts and M6 back-mount drawing: use hole locations/depths from the original diagram; accessory payload and screw torque remain unverified.                   | [Unitree image 7](https://doc-cdn.unitree.com/static/2026/7/3/cc00b9dff3004df09c6944c34398bb0d_2481x3509.png)  |
| 8           | H2/H2 EDU mechanical comparison: 31 body joints, optional hands, maximum torques and payload conditions; preserve base/EDU differences.                            | [Unitree image 8](https://doc-cdn.unitree.com/static/2026/7/3/621055a624eb448c96deaf50dc555a5a_2481x3509.png)  |
| 9           | Electrical/compute comparison: maximum 75.6 V battery, i5/i7 scope and EDU development distinction; optional compute is not standard equipment.                    | [Unitree image 9](https://doc-cdn.unitree.com/static/2026/7/3/d6a1255b4a3a44509c8dc328f3f7c49c_2481x3509.png)  |
| 10          | Interface top-view map and first table rows: numbered direct battery, 24 V/CAN and 12 V/RS-485 ports; orientation is not a cable mating view.                      | [Unitree image 10](https://doc-cdn.unitree.com/static/2026/7/3/3dd74f7335814d4bb380078aa1b77b9c_2481x3509.png) |
| 11          | USB-C routing depends on PC2/PC3/PC4 configuration; two Ethernet subnet families and optional hand-interface variants need actual configuration.                   | [Unitree image 11](https://doc-cdn.unitree.com/static/2026/7/3/8c1217d661004f6091f7e9fea39405e1_2482x3509.png) |
| 12          | External output budget, direct battery range, shared RS-485 buses and connector front/back pinout diagrams; retain the visible 458\_B label ambiguity.             | [Unitree image 12](https://doc-cdn.unitree.com/static/2026/7/3/b69a5c188c444438b0f6f5152476325b_2482x3509.png) |
| 13          | Robot battery charging requires a removed, off pack and matched genuine charger; AC-before-battery instruction needs reconciliation with shipping activation text. | [Unitree image 13](https://doc-cdn.unitree.com/static/2026/7/3/e53e01ab5f6b4e55b323fde89c97b752_2481x3509.png) |
| 14          | Cooling before charge and remote USB charging; remote full indication differs from robot-pack indication, so do not combine LED tables.                            | [Unitree image 14](https://doc-cdn.unitree.com/static/2026/7/3/e7572890231a4f9cb1c50c5c220888e9_2481x3508.png) |
| 15          | Environment, terrain, clearance and unboxing: H2 is not waterproof/dustproof; protective stand and lanyard are part of the handling workflow.                      | [Unitree image 15](https://doc-cdn.unitree.com/static/2026/7/3/68919017b4a746269da7a4471d040f6a_2481x3508.png) |
| 16          | Shipping-mode text, pre-start inspection and shoulder-latch suspension; activation connection order differs from general charging instructions.                    | [Unitree image 16](https://doc-cdn.unitree.com/static/2026/7/3/33705b3dfc954b06924abae449a2e312_2482x3508.png) |
| 17          | Battery insertion orientation/latch and suspended startup pose; do not force the pack or place fingers near moving joints.                                         | [Unitree image 17](https://doc-cdn.unitree.com/static/2026/7/3/2bde687feea44ea4bc657dc65667d744_2482x3508.png) |
| 18          | Startup pose determines upper-limb/ankle zero positions; robot power-button timing differs from the standalone battery manual.                                     | [Unitree image 18](https://doc-cdn.unitree.com/static/2026/7/3/835f304d6cc64fa4a88c6dbdd7946aa1_2481x3508.png) |
| 19          | Approximately 120-second initialization and ready/ground transition illustration; not an authorized first software test.                                           | [Unitree image 19](https://doc-cdn.unitree.com/static/2026/7/3/7a12b8ba8f8d4d43981cacb34737e985_2481x3508.png) |
| 20          | Post-startup emergency summary says press L2+B for damping/descent without a hold duration; distinguish §5.6 timed soft stop and debug-mode repeat behavior.       | [Unitree image 20](https://doc-cdn.unitree.com/static/2026/7/3/8bf2263d96874be493051792510804d1_2481x3508.png) |
| 21          | Explore Add Robot and Bluetooth permissions/account binding; generic app model text does not establish every H2 UI label.                                          | [Unitree image 21](https://doc-cdn.unitree.com/static/2026/7/3/9e24187f9f944613a42886fca25ddddc_2481x3508.png) |
| 22          | AP direct-connect screenshots; illustrative credentials are not a verified per-unit default or permission to change binding.                                       | [Unitree image 22](https://doc-cdn.unitree.com/static/2026/7/3/6674f8f4e31d44ad80affeeddf72fd8a_2482x3508.png) |
| 23          | Router Wi-Fi flow and optional internet remote connection; network access and software update are separate from a passive state read.                              | [Unitree image 23](https://doc-cdn.unitree.com/static/2026/7/3/22ff229251bb42cb83b4af2d087b062f_2482x3508.png) |
| 24          | Account-unbind UI example; example screenshot references another model and unbinding changes control access.                                                       | [Unitree image 24](https://doc-cdn.unitree.com/static/2026/7/3/d082fef7c40449de9e9b687edc64dca7_2481x3508.png) |
| 25          | GO opens an operating interface; remote binding uses the controller ID and a pairing/restart flow; not needed for offline checks.                                  | [Unitree image 25](https://doc-cdn.unitree.com/static/2026/7/3/c02e89ea6ee548e490d581f6aaaf3076_2481x3508.png) |
| 26          | Soft stop explicitly holds L2+B more than5seconds for damped descent; hard stop describes power loss/direct fall. Both need firmware/controller qualification.     | [Unitree image 26](https://doc-cdn.unitree.com/static/2026/7/3/9565c2ad421747ce810fea1bce0fa733_2481x3508.png) |
| 27          | Hard-stop restart timing and head indicator colors distinguish startup, recording, balance, damping, seated, debug, zero-torque and ready modes.                   | [Unitree image 27](https://doc-cdn.unitree.com/static/2026/7/3/4d0c250cfdad478d95c180f013bc67bd_2481x3508.png) |
| 28          | In suspended/debug context the first L2+B enters damping and the second enters zero torque; not a universal stop toggle or holding guarantee.                      | [Unitree image 28](https://doc-cdn.unitree.com/static/2026/7/3/90cbc283b29d49ae97a2a6e744543636_2482x3508.png) |
| 29          | Calibration points to an external video; shutdown requires resuspension and damping before battery power off; video content was not read.                          | [Unitree image 29](https://doc-cdn.unitree.com/static/2026/7/3/e9eb79f840764bed84adced4927be1d6_2482x3508.png) |
| 30          | Packing sequence and posture illustration; use the protective foam/case and exact handling procedure rather than extrapolating folded dimensions.                  | [Unitree image 30](https://doc-cdn.unitree.com/static/2026/7/3/0040d5f18c584e4cbab13beed2ba1017_2481x3508.png) |
| 31          | Faults: failed initialization, fall protection, AP/Wi-Fi issues, failed remote module and incorrect startup posture; preserve safe suspension in recovery.         | [Unitree image 31](https://doc-cdn.unitree.com/static/2026/7/3/061c0049bf4b4c4cba3abb28e0552c35_2481x3508.png) |
| 32          | Factory-calibration caution, standby suspension and runtime/speed conditions; 3 m/s is configuration-specific and practically limited.                             | [Unitree image 32](https://doc-cdn.unitree.com/static/2026/7/3/8d721c002f64495e82154632ac96c170_2481x3508.png) |
| 33          | Powered-off cleaning, dry storage and mechanical/battery/remote/cooling checks; no water or solvent maintenance is inferred.                                       | [Unitree image 33](https://doc-cdn.unitree.com/static/2026/7/3/124471a4d2d94dab966c31d428211fe4_2481x3508.png) |
| 34          | Powered checks, storage-charge guidance and beginning of foot-airbag replacement; powered functional inspection is separate from offline research.                 | [Unitree image 34](https://doc-cdn.unitree.com/static/2026/7/3/bda28e0f33784f968cbcc93dc0215202_2482x3508.png) |
| 35          | Foot-airbag diagram distinguishes eight removable bolts from two bolts to loosen only; retain the original figure for servicing.                                   | [Unitree image 35](https://doc-cdn.unitree.com/static/2026/7/3/500ef05e7fa24eeca5e7776872d7eeaf_2482x3508.png) |
| 36          | Reassembly and warranty scope: 8 months H2 / 12 months EDU in this manual; unauthorized modifications may affect service.                                          | [Unitree image 36](https://doc-cdn.unitree.com/static/2026/7/3/b05bd99b9a254ac291156d63235275c0_2481x3508.png) |
| 37          | Industry Canada and FCC notices; source claims are not a new compliance assessment for a modified robot.                                                           | [Unitree image 37](https://doc-cdn.unitree.com/static/2026/7/3/519e821911474910a303eafa8b56f4cb_2481x3508.png) |
| 38          | RF bands/power and regional indoor-use statements; keep exact radio variant and current regional requirements with deployment review.                              | [Unitree image 38](https://doc-cdn.unitree.com/static/2026/7/3/0cc7351ecfaf46fab3c130a2a0f1f94a_2481x3508.png) |
| 39          | ANATEL/regional notices and revision history: V1.1 July 2, 2026 adds foot-airbag guidance, interface update and certification content.                             | [Unitree image 39](https://doc-cdn.unitree.com/static/2026/7/3/c71f38d4ac2d4eaea9675f17d02c885a_2481x3508.png) |

#### H2 Emergency Stop Remote Manual V1.0 <a href="#h2-emergency-stop-remote-manual-v10" id="h2-emergency-stop-remote-manual-v10"></a>

[Official image-based article](https://marketing.unitree.com/article/en/H2/Remote_Control.html). No PDF URL is inferred.

| Source page | Original engineering interpretation / figure purpose                                                                                                    | Original source image                                                                                          |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| 1           | Cover identifies H2 Emergency Stop Remote Control User Manual V1.0; no H2-X/G1+ applicability established.                                              | [Unitree image 1](https://doc-cdn.unitree.com/static/2026/6/3/0a61d599c58f4e27b9173c5182accc65_2481x3508.png)  |
| 2           | R3 introduction and labeled parts: data link, Bluetooth and emergency-stop unit are distinct subsystems.                                                | [Unitree image 2](https://doc-cdn.unitree.com/static/2026/6/3/196ad583a53d4179947bda3de11c598e_2481x3508.png)  |
| 3           | Specifications and joystick installation: 5 V, 700 mA, 780 mAh, about 5 h, above 100 m in an open environment; no guaranteed obstructed range.          | [Unitree image 3](https://doc-cdn.unitree.com/static/2026/6/3/78e137e1f24f47958753d22e1cfdcb5c_2481x3508.png)  |
| 4           | Joystick calibration, power sequence and sound/vibration toggle; calibration is an active operator procedure, not an offline first result.              | [Unitree image 4](https://doc-cdn.unitree.com/static/2026/6/3/9555230400ee4139b3de389e1e8995a4_2481x3508.png)  |
| 5           | Feedback persistence and emergency-stop toggle: red/green state, three-second lockout, flashing link means stop unit not connected.                     | [Unitree image 5](https://doc-cdn.unitree.com/static/2026/6/3/d16933718480407b9d2415277ee9b7b1_2482x3508.png)  |
| 6           | Powered-off Type-C charging with recommended 5 V/2 A adapter; App binding entry begins.                                                                 | [Unitree image 6](https://doc-cdn.unitree.com/static/2026/6/3/2518ca72551a49b1a7870074dfd56572_2482x3508.png)  |
| 7           | Controller-ID binding and DL indication; read the button labels in the original figure before operating a real controller.                              | [Unitree image 7](https://doc-cdn.unitree.com/static/2026/6/3/1df78bcf96d54ac5bf907b5716c54075_2481x3508.png)  |
| 8           | Joystick-direction illustration and obstacle attenuation; this is commanded motion, not status reading.                                                 | [Unitree image 8](https://doc-cdn.unitree.com/static/2026/6/3/bc1886cc4fd34486989ff730bdb8bed6_2481x3508.png)  |
| 9           | Mode/interaction key chart; glyphs require the original image and matching firmware overlay. No key-chart action is used by this guide.                 | [Unitree image 9](https://doc-cdn.unitree.com/static/2026/6/3/cd2ec12baedf448186785881977e77c7_2481x3508.png)  |
| 10          | Emergency stop attempts squat then zero torque after 1.5 s, unlike user-manual direct-power-loss wording; restart required. Revision V1.0 May 29, 2026. | [Unitree image 10](https://doc-cdn.unitree.com/static/2026/6/3/3331423e3a524d68968e42c8e82fbf79_2481x3508.png) |

#### H2 Battery and Charger Manual V1.1 <a href="#h2-battery-and-charger-manual-v11" id="h2-battery-and-charger-manual-v11"></a>

[Official image-based article](https://marketing.unitree.com/article/en/H2/Battery_Charger.html). No PDF URL is inferred.

| Source page | Original engineering interpretation / figure purpose                                                                                                                                    | Original source image                                                                                           |
| ----------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| 1           | Cover identifies H2 Battery and Charger User Manual V1.1; not a universal humanoid pack manual.                                                                                         | [Unitree image 1](https://doc-cdn.unitree.com/static/2026/6/17/9c6394412e44444999589cbc7ace5553_2482x3508.png)  |
| 2           | Pack/charger introduction and dimension illustration; shipping activation text reverses general charging connection order.                                                              | [Unitree image 2](https://doc-cdn.unitree.com/static/2026/6/17/a281e20ccaa24a0bbe016cdb5f1a9620_2481x3508.png)  |
| 3           | Pack parts and specifications: 207 × 222.8 × 84 mm, nominal 64.8 V, limit 75.6 V, 15 Ah/0.972 kWh; BMS reserves affect usable capacity.                                                 | [Unitree image 3](https://doc-cdn.unitree.com/static/2026/6/17/8624aec23a2242f7bc5d9368397a63c0_2481x3508.png)  |
| 4           | Charger table visibly prints 76.5 V, conflicting with 75.6 V pack limit; 100–240 V AC input, 2 h 40 min at 25°C, protection functions and load detection.                               | [Unitree image 4](https://doc-cdn.unitree.com/static/2026/6/17/5f3d78f7f0e24345b659cca06a423ab4_2481x3508.png)  |
| 5           | LED power-level tables depend on off/insertion/discharge state; the original color/shape legend is needed for diagnosis.                                                                | [Unitree image 5](https://doc-cdn.unitree.com/static/2026/6/17/beb0b4c449c341f9ab056c5b861588e7_2481x3508.png)  |
| 6           | Battery button timing says more than 3 s; charging requires off/removed pack and AC first, then battery, then cooling/full-charge disconnection.                                        | [Unitree image 6](https://doc-cdn.unitree.com/static/2026/6/17/d355a636e25042028efbb0938a94d18a_2482x3508.png)  |
| 7           | Charging connection figure and charging/protection LED legend; use exact row/LED orientation from the original image.                                                                   | [Unitree image 7](https://doc-cdn.unitree.com/static/2026/6/17/dfd55371bd9c4d0982d62c0f5dd47d39_2482x3508.png)  |
| 8           | Protection display distinguishes damage, temperature, voltage, current, short circuit, communication failure and shipping mode; fault cause must be resolved first.                     | [Unitree image 8](https://doc-cdn.unitree.com/static/2026/6/17/6b01ea34f09a40a89c177f2c5a421681_2481x3508.png)  |
| 9           | Use guidance, lower-charge replacement threshold, no live insertion/removal, no damaged/impacted packs and model-specific handling; battery temperature is not whole-robot temperature. | [Unitree image 9](https://doc-cdn.unitree.com/static/2026/6/17/cca9bed21f2b411599ccd9a1f72c898d_2481x3508.png)  |
| 10          | Charging, cleaning, official-adapter and storage constraints; supervise a cooled pack away from combustible material.                                                                   | [Unitree image 10](https://doc-cdn.unitree.com/static/2026/6/17/cac00ea50f7747f0924a373b06a78fb3_2481x3508.png) |
| 11          | Transport/storage/maintenance/disposal and revision: check stored charge, no damaged-pack transport; V1.1 June 17, 2026 adds shipping-mode indicator.                                   | [Unitree image 11](https://doc-cdn.unitree.com/static/2026/6/17/8d8e711e83ae4768b55755bfeab52d3e_2481x3508.png) |

#### Battery, indicator and maintenance interpretation <a href="#battery-indicator-and-maintenance-interpretation" id="battery-indicator-and-maintenance-interpretation"></a>

The battery manual’s protection thresholds describe BMS behavior, not approved routine operating targets. Section 4 lists charge-temperature rejection below 0°C or above 50°C, charging-overcurrent protection above 18 A, discharge cutoff at 50.4 V, and an approximately 300 mA pre-charge stage when voltage is below 45 V until recovery to 50.4 V. Do not intentionally approach these thresholds, force a depleted pack awake or override a protection fault. The same manual recommends room-temperature cooling before charging and an ideal charge environment of 5–40°C. The whole H2 remains limited by its own 0–40°C environment instruction.

The pack’s LED tables differ among off/not-inserted, off/inserted, discharging, charging and protection states. Compare the actual LED1–LED4 positions and color/blink legend to original battery source pages 3 and 5–8. A percentage row whose symbols are unclear is not a reliable diagnostic table. Section 8 distinguishes a charger fault indicated during charging from discharge protection and a communication fault requiring factory attention. Capture the exact pattern and component labels; do not short contacts or use an external cable to bypass pack detection.

Battery source pages 9–11 discuss genuine undamaged packs, no live insertion/removal, avoiding liquids/impact/short circuit, supervised charging, dry storage, charge checks, transport and disposal. They recommend ending use below 40% and checking stored packs below 30% for recharge to 70%. The broad standalone battery use range of −20°C to 70°C is not permission to use H2 outside its whole-robot limits. Transport wording around 65% is preserved only in the original; qualified shipping requirements must be checked for the actual pack and route. No battery is discharged or charged as part of this guide.

For the R3 remote, source pages 3–7 distinguish its 5 V / 700 mA charging specification from the recommended 5 V / 2 A USB adapter capability, its 780 mAh battery and approximately 5 h runtime. The joystick calibration procedure, power gestures, F1/F3 sound/vibration settings and shutdown-save behavior are separate operator functions. Pages 8–9 contain joystick directions, mode controls and gestures including handshake, wave, refusal and other interaction actions. Use the original chart and matching firmware overlay; this index does not reconstruct unreadable button glyphs or execute gestures. An idle unconnected remote may shut down after ten minutes; a lit data-link indicator and an independently linked stop unit are different checks.

User source pages 27–32 distinguish head status colors, debug ownership, factory calibration, shutdown, packing and recovery. A yellow debug indicator is not a universal firmware compatibility check. The guide intentionally does not replay posture-changing mode confirmation, stand or arm actions. The calibration chapter references a video that has not been read; no fixture-by-fixture calibration procedure is invented. Foot-airbag service on source pages 34–36 requires the original bolt-location figures and an appropriately qualified service workflow.

### Portal article and functional-section index <a href="#portal-article-and-functional-section-index" id="portal-article-and-functional-section-index"></a>

The following index covers the supplied exact collection, including empty navigation nodes. It points to original-English engineering interpretation above; it does not republish manual transcripts, SDK source bundles or unviewed media. A linked figure, video, CAD archive or driver package is a separate evidence boundary.

| Actual article                                                                                     | Applicability/read state       | Guide destination                                                                                       |
| -------------------------------------------------------------------------------------------------- | ------------------------------ | ------------------------------------------------------------------------------------------------------- |
| [About H2](https://doc-cdn.unitree.com/25/1061/en/25_1061_en)                                      | Read with model/version limits | [Interpretation and boundary](unitree-h2.md#portal-electrical-routing-and-the-shared-peripheral-budget) |
| [Operational Guidance](https://doc-cdn.unitree.com/25/1101/en/25_1101_en)                          | Index only                     | [Interpretation and boundary](unitree-h2.md#downloads-and-technical-documents)                          |
| [Quick Start](https://doc-cdn.unitree.com/25/1102/en/25_1102_en)                                   | Read with model/version limits | [Interpretation and boundary](unitree-h2.md#versioned-remote-controls-and-ownership-boundaries)         |
| [Remote Control Guide](https://doc-cdn.unitree.com/25/1103/en/25_1103_en)                          | Read with model/version limits | [Interpretation and boundary](unitree-h2.md#versioned-remote-controls-and-ownership-boundaries)         |
| [Dexterous Hand Disassembly and Assembly Guide](https://doc-cdn.unitree.com/25/1553/en/25_1553_en) | Read with model/version limits | [Interpretation and boundary](unitree-h2.md#h2-hand-installation-and-compatible-routing-choices)        |
| [SDK Application Development](https://doc-cdn.unitree.com/25/1104/en/25_1104_en)                   | Index only                     | [Interpretation and boundary](unitree-h2.md#downloads-and-technical-documents)                          |
| [SDK Overview](https://doc-cdn.unitree.com/25/1105/en/25_1105_en)                                  | Read with model/version limits | [Interpretation and boundary](unitree-h2.md#ddsrpc-transport-architecture-and-host-preparation)         |
| [Architecture Description](https://doc-cdn.unitree.com/25/1106/en/25_1106_en)                      | Read with model/version limits | [Interpretation and boundary](unitree-h2.md#ddsrpc-transport-architecture-and-host-preparation)         |
| [Access Resources](https://doc-cdn.unitree.com/25/1264/en/25_1264_en)                              | Read with model/version limits | [Interpretation and boundary](unitree-h2.md#ddsrpc-transport-architecture-and-host-preparation)         |
| [Quick Development](https://doc-cdn.unitree.com/25/1107/en/25_1107_en)                             | Read with model/version limits | [Interpretation and boundary](unitree-h2.md#ddsrpc-transport-architecture-and-host-preparation)         |
| [Motion Control Development](https://doc-cdn.unitree.com/25/1114/en/25_1114_en)                    | Index only                     | [Interpretation and boundary](unitree-h2.md#downloads-and-technical-documents)                          |
| [Basic Motion Development](https://doc-cdn.unitree.com/25/1115/en/25_1115_en)                      | Index only                     | [Interpretation and boundary](unitree-h2.md#downloads-and-technical-documents)                          |
| [Joint Motor Sequence](https://doc-cdn.unitree.com/25/1117/en/25_1117_en)                          | Read with model/version limits | [Interpretation and boundary](unitree-h2.md#h2-message-layout-and-high-level-version-boundaries)        |
| [Basic Services Interface](https://doc-cdn.unitree.com/25/1132/en/25_1132_en)                      | Read with model/version limits | [Interpretation and boundary](unitree-h2.md#h2-message-layout-and-high-level-version-boundaries)        |
| [Remote Control Data](https://doc-cdn.unitree.com/25/1119/en/25_1119_en)                           | Read with model/version limits | [Interpretation and boundary](unitree-h2.md#versioned-remote-controls-and-ownership-boundaries)         |
| [High Motion Development](https://doc-cdn.unitree.com/25/1116/en/25_1116_en)                       | Index only                     | [Interpretation and boundary](unitree-h2.md#downloads-and-technical-documents)                          |
| [RPC Routine](https://doc-cdn.unitree.com/25/1120/en/25_1120_en)                                   | Read with model/version limits | [Interpretation and boundary](unitree-h2.md#h2-message-layout-and-high-level-version-boundaries)        |
| [Sport Services Interface](https://doc-cdn.unitree.com/25/1133/en/25_1133_en)                      | Read with model/version limits | [Interpretation and boundary](unitree-h2.md#h2-message-layout-and-high-level-version-boundaries)        |
| [Odometer Service Interface](https://doc-cdn.unitree.com/25/1121/en/25_1121_en)                    | Read with model/version limits | [Interpretation and boundary](unitree-h2.md#odometry-frame-clock-and-service-prerequisites)             |
| [Services Interface](https://doc-cdn.unitree.com/25/1122/en/25_1122_en)                            | Index only                     | [Interpretation and boundary](unitree-h2.md#downloads-and-technical-documents)                          |
| [DDS Services Interface](https://doc-cdn.unitree.com/25/1123/en/25_1123_en)                        | Read with model/version limits | [Interpretation and boundary](unitree-h2.md#ddsrpc-transport-architecture-and-host-preparation)         |
| [VuiClient Service Interface](https://doc-cdn.unitree.com/25/1126/en/25_1126_en)                   | Read with model/version limits | [Interpretation and boundary](unitree-h2.md#audio-speech-and-multimedia-interfaces)                     |
| [Bilateral Data Stream Acquisition Interface](https://doc-cdn.unitree.com/25/1265/en/25_1265_en)   | Read with model/version limits | [Interpretation and boundary](unitree-h2.md#pc1-stereo-streams-and-depth-interpretation)                |
| [Multimedia\_Services](https://doc-cdn.unitree.com/25/1443/en/25_1443_en)                          | Read with model/version limits | [Interpretation and boundary](unitree-h2.md#audio-speech-and-multimedia-interfaces)                     |
| [H2Plus GMSL camera interface](https://doc-cdn.unitree.com/25/1576/en/25_1576_en)                  | Read with model/version limits | [Interpretation and boundary](unitree-h2.md#h2plus-optional-thor-gmsl-and-calibration-boundaries)       |
| [More Cases](https://doc-cdn.unitree.com/25/1128/en/25_1128_en)                                    | Index only                     | [Interpretation and boundary](unitree-h2.md#downloads-and-technical-documents)                          |
| [Ros2 Communication Routine](https://doc-cdn.unitree.com/25/1130/en/25_1130_en)                    | Read with model/version limits | [Interpretation and boundary](unitree-h2.md#ddsrpc-transport-architecture-and-host-preparation)         |
| [DDS Communication Routine](https://doc-cdn.unitree.com/25/1131/en/25_1131_en)                     | Read with model/version limits | [Interpretation and boundary](unitree-h2.md#ddsrpc-transport-architecture-and-host-preparation)         |
| [Debugging Specification](https://doc-cdn.unitree.com/25/1260/en/25_1260_en)                       | Read with model/version limits | [Interpretation and boundary](unitree-h2.md#versioned-remote-controls-and-ownership-boundaries)         |

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

The current portal expansion reviews 29 supplied records for this collection, preserving exact-model/shared-service/other-model distinctions and source/API mismatches. Existing manual page indexes and source-specific safety/power statements remain in place. No vendor source, SDK, ROS, DDS, simulator, physical hardware, charging, motion, calibration or flashing was executed. Only original offline parsing/AST/synthetic checks are validation evidence.

Reviewed November 24, 2026: [H2 product page](https://www.unitree.com/H2/), the three English manual articles above, H2 app entry and pinned SDK2 source. The appendix gives original chapter summaries and links to the manufacturer’s page images. This is original engineering interpretation with source links, not a reproduction of the manuals.

**Readiness:** source-bounded draft for physical commissioning. Critical remaining items are approved charger/activation instructions, actual stop behavior and controller revision, firmware pairing, exact developer entitlement, per-unit network and optional interface configuration. H2 developer articles and videos not reviewed here do not establish any additional compatibility.

**Offline validation:** the standalone seven-case synthetic example was executed successfully; source inspection remains distinct from robot testing. **Software execution:** Unitree SDK installation/build/import, DDS, ROS and vendor examples not run. **Hardware validation:** not run; no power, charging, motion, calibration or flashing performed. Store identity is limited to the observed H2/H2 EDU listing and SKU matches.

**Related documentation:** [Unitree model and development directory](./).

**Related documentation:** [Unitree model and development directory](./).
