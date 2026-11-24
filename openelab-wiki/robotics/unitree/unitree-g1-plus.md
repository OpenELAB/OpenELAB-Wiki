---
description: >-
  Distinguish G1+ from base G1, compare 25–45 DoF options and upgraded sensing,
  and check model evidence offline while exact manuals, power wiring and SDK
  pairing remain unresolved.
---

# Unitree G1+ and G1+ EDU: configuration, power and development evidence

{% hint style="info" %}
**Manufacturer reference: Unitree G1+ / G1+ EDU.** No exact OpenELAB SKU or product URL was observed in the reviewed store listings. The store match remains unverified; base G1 store listings are not purchasing matches for G1+.

**Identity:** the manufacturer's G1+ page is at `G1pl`; the `+` denotes a distinct named product. It is not an alias for G1, G1 EDU or G1-D.
{% endhint %}

## Product overview <a href="#product-overview" id="product-overview"></a>

Unitree G1+ is a compact humanoid with two powered neck axes, revised motors, binocular and chest wide-angle vision, head touch sensing and expanded audio interaction. Its base model has 25 published joint motors; G1+ EDU spans 25–45 depending on configuration. This guide explains those differences and provides an offline configuration/evidence checkpoint. Live SDK compatibility, charging and commissioning remain **source-bounded draft** topics until exact G1+ manuals, firmware and hardware interfaces are verified. [Official G1+ page](https://www.unitree.com/G1pl/)

The product page lists secondary development as slash for G1+ and Yes for G1+ EDU. Optional waist axes, wrist axes, hands and compute cannot be inferred from an EDU label alone. A base-G1 23/29-joint example, G1 hand program or G1 network guide does not establish a G1+ joint map or software target. The official model catalog explicitly names `g1_pl.urdf`, but a model asset is evidence of a description variant, not a physical DDS/firmware contract. [Pinned model catalog](https://github.com/unitreerobotics/unitree_ros/blob/157ff950351e5f535e03c5d85a16b7d594b3dbcc/README.md)

### What the G1+ portal now establishes <a href="#what-the-g1-portal-now-establishes" id="what-the-g1-portal-now-establishes"></a>

All **37 supplied G1+ developer records** have now been reviewed. The new exact-model About, head-control, external-power and voice chapters add useful evidence, while several older chapters still explicitly describe G1 23/29-DoF hardware. Being filed under G1+ does not silently change those older examples into G1+ operating procedures. Empty categories are identified in the source crosswalk, and all prior product facts, figure links and synthetic checks remain below. [About G1+](https://doc-cdn.unitree.com/39/1623/en/39_1623_en), [head interface](https://doc-cdn.unitree.com/39/1660/en/39_1660_en).

The product's **25–45 DoF** offering, the specific **31-body-joint URDF**, the **35-entry HG body array**, and optional hand messages describe different scopes. A 25-joint body has twelve leg, ten arm, one waist and two head joints; optional two-axis waist expansion and two extra wrist axes per arm yield a 31-body-joint configuration. Two seven-actuator hands can add fourteen axes to reach45. Those hands are not fourteen extra body-array entries, and no body decoder has 45 motors merely because a product option reaches45.

## Applications <a href="#applications" id="applications"></a>

* **Configuration and kinematics research:** G1+ EDU's head, optional waist and hand arrangements make it important to compare the purchased bill of materials with a specific description file before planning transforms or reach. A generic G1 mesh is insufficient.
* **Perception and multimodal interaction:** binocular vision, chest wide-angle sensing, tactile input and a six-microphone array support supervised sensing/interaction experiments. Camera calibration, timestamps, touch-event API and audio access still need model-specific documentation.
* **Long-duration supervised demonstrations:** the product advertises external runtime power and charging. This is a potential system feature, not a wiring recipe or guarantee of unlimited thermal/compute endurance.

These are engineering interpretations of the documented features. No unattended operation, human-contact safety certification, calibrated touch-force measurement or production autonomy is established. The manufacturer notes that some functions remain under development and that specifications depend on configuration. [G1+ features and notes](https://www.unitree.com/G1pl/)

## Specifications <a href="#specifications" id="specifications"></a>

The following values belong to the G1+ manufacturer page, not base G1. The page is undated and was read November 24, 2026. [Official G1+ specification table](https://www.unitree.com/G1pl/)

| Parameter                           | G1+                                                                     | G1+ EDU / qualification                                                                          |
| ----------------------------------- | ----------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| Standing height × width × thickness | 1340 × 450 × 200 mm                                                     | Same published dimensions                                                                        |
| Folded height × width × thickness   | 690 × 450 × 300 mm                                                      | Same; no folding sequence or pinch-clearance procedure verified                                  |
| Mass including battery              | About 35 kg                                                             | About 35 kg+; options change mass                                                                |
| Joint motors / DoF                  | 25                                                                      | 25–45, configuration dependent                                                                   |
| Head / each leg / each arm          | 2 / 6 / 5                                                               | Same base body rows                                                                              |
| Waist                               | 1 DoF                                                                   | 1, or optional 3 DoF                                                                             |
| Each hand / added wrist axes        | Slash                                                                   | 7 hand DoF (different hands available), plus 2 optional wrist DoF; confirm actual purchased hand |
| Arm maximum load                    | About 3 kg                                                              | About 4 kg; strongly dependent on arm extension posture, not a universal rated payload           |
| Calf + thigh / arm span             | 0.6 m / about 0.45 m                                                    | Retain the manufacturer's “arm span” wording; do not reinterpret as full wingspan                |
| Joint hardware                      | Crossed-roller bearings, low-inertia internal-rotor PMSM, dual encoders | No standalone actuator replacement contract established                                          |
| Cooling / electrical routing        | Local air cooling; hollow joint routing                                 | Neither establishes an ingress rating or accessible user wiring                                  |
| Battery / capacity                  | 13-series lithium pack; quick-release 9000 mAh                          | Nominal voltage/energy are not specified in the reviewed table                                   |
| Charger table row                   | 54 V, 5 A                                                               | Not a verified external runtime supply specification                                             |
| Runtime                             | About 2 h                                                               | Workload dependent; external power does not remove all operating limits                          |
| Compute                             | 8-core high-performance CPU                                             | Optional additional module choices such as Orin; exact model not fixed                           |
| Sensing                             | Binocular camera + chest wide-angle camera + 3D LiDAR                   | No LiDAR model/range or calibration contract verified                                            |
| Audio                               | Six-microphone array; two 10 W speakers                                 | Feature panel places speakers at waist                                                           |
| Radio / OTA                         | Wi-Fi 6, Bluetooth 5.2; smart OTA Yes                                   | No firmware version pairing inferred                                                             |
| Manual controller                   | Yes                                                                     | Controller model/stop protocol unresolved                                                        |
| Secondary development               | Slash                                                                   | Yes, with model-specific manual required                                                         |
| Warranty reference                  | 8 months                                                                | 18 months; actual sale terms apply                                                               |

### Motion ranges and motor upgrades <a href="#motion-ranges-and-motor-upgrades" id="motion-ranges-and-motor-upgrades"></a>

The head panel gives pitch **−25° to +36°**, yaw **±110°**. The table separately gives waist Z **±155°**, knee **0–165°**, hip pitch **±154°**, roll **−30° to +170°**, yaw **±158°**; the EDU column adds wrist pitch/yaw **±92.5°**. These are advertised movement-space values, not a validated safe command envelope. Coordinate zero, collision margins, installed joint set and firmware limits remain essential. Do not command these extremes from this guide. [G1+ movement-space rows](https://www.unitree.com/G1pl/)

G1+'s upgrade panel reports shoulder/waist peak torque **+110%**, arm peak torque **+43%**, and lower heat generation at the same torque (shoulder/waist −72%, arm −30%, thigh −28%). The reviewed panel supplies neither an absolute N·m rating nor the full comparison test conditions. Do not multiply an old G1 specification to manufacture a new G1+ torque limit. [G1+ motor-upgrade panel](https://www.unitree.com/G1pl/)

### Camera, touch and voice details <a href="#camera-touch-and-voice-details" id="camera-touch-and-voice-details"></a>

The binocular panel specifies a **60 mm baseline**, **2 MP**, central resolution **≥500 LW/PH** and FOV **H110° / V80° / D125°**. LW/PH means line widths per picture height; it is an optical resolution descriptor, not depth accuracy. The chest monocular stream is **1920 × 1080 at 30 fps**, FOV **H117° / V67°**. No stereo-depth range, depth frame rate or calibrated depth precision is established. The six microphones are arranged four front and two rear with direction-of-arrival localization; external wireless microphones are supported in the feature text. [G1+ perception and audio panels](https://www.unitree.com/G1pl/)

The original feature illustration additionally labels **five head touch points**, dual **2 MP global-shutter cameras**, a wireless microphone charging case, **50 m transmission range** and **80 dB signal-to-noise ratio**. Those microphone accessory figures do not describe the robot's Wi-Fi range or a guaranteed noisy-room performance. The same figure labels a rear external input **DC 54.6 V, ≤7.4 A**; this differs from the table's charger row and must be treated as a separate interface claim requiring exact instructions. [Original Unitree G1+ feature figure](https://www.unitree.com/images/32be40654390458795e906bb649c532c_2000x1346.png?x-oss-process=image/format,webp)

### Portal specifications and revision differences <a href="#portal-specifications-and-revision-differences" id="portal-specifications-and-revision-differences"></a>

The current About chapter describes1340×450×200 mm standing and 690×450×300 mm folded dimensions, approximately 35 kg base /35 kg+ EDU, a13-series9000mAh battery,54 V/5 A charger entry, approximately 2 h runtime, six microphones, two 10 W speakers, Wi-Fi6 and Bluetooth5.2. The portal's EDU arm-payload entry is approximately **3 kg**, while the separately reviewed living product page gives **4 kg**. Preserve both as revision/configuration claims; neither is a validated continuous all-posture load envelope. A source maximum120 N·m joint claim, a URDF effort value121 and per-joint controller limits have different meanings. [About](https://doc-cdn.unitree.com/39/1623/en/39_1623_en).

The exact-model portal map includes head pitch/yaw at **29/30**. Optional waist 13/14 and optional wrist20/21/27/28 must be matched to actual hardware. The joint chapter's table headers say23 DoF and 29 DoF, yet their populated body rows include the head and count **25/31**; another14 DoF header similarly contains 16populated rows. Its `mode_machine` labels1/2/9 also conflict with the Basic Services chapter's4/5/6 comments. These source inconsistencies are not a configuration-selection recipe. Read the delivered mode and explicit physical map; do not write a guessed model number. [Joint sequence](https://doc-cdn.unitree.com/39/1641/en/39_1641_en), [basic services](https://doc-cdn.unitree.com/39/1645/en/39_1645_en).

The illustrated Dex3-1 is a separate seven-actuator hand,12–58 V, nine sensor arrays,10–2500g sensing range. Thumb intervals are0–100°,−35–60°,−60–60°; index/middle are0–90° and 0–100°. These are hand-specific ranges, not arm payload or permission to use an arbitrary12–58 V source. Array sensor count, per-pad data length and actuator count must not be conflated.

### Full-body portal joint-limit reference, with optional axes <a href="#full-body-portal-joint-limit-reference-with-optional-axes" id="full-body-portal-joint-limit-reference-with-optional-axes"></a>

The following numerical intervals are source-reference radians for the illustrated full body. They are not approved combined targets, actuator-space AB limits or a collision-free motion envelope. Optional axes require actual configuration matching; do not infer physical joints from missing/padded transport slots. [Original joint reference](https://doc-cdn.unitree.com/39/1623/en/39_1623_en).

| Source ID | Exact source joint identifier | Reference interval, rad     |
| --------- | ----------------------------- | --------------------------- |
| `0`       | `L_LEG_HIP_PITCH`             | -2.5307 to 2.8798           |
| `1`       | `L_LEG_HIP_ROLL`              | -0.5236 to 2.9671           |
| `2`       | `L_LEG_HIP_YAW`               | -2.7576 to 2.7576           |
| `3`       | `L_LEG_KNEE`                  | -0.087267 to 2.8798         |
| `4`       | `L_LEG_ANKLE_PITCH`           | -0.87267 to 0.5236          |
| `5`       | `L_LEG_ANKLE_ROLL`            | -0.2618 to 0.2618           |
| `6`       | `R_LEG_HIP_PITCH`             | -2.5307 to 2.8798           |
| `7`       | `R_LEG_HIP_ROLL`              | -2.9671 to 0.5236           |
| `8`       | `R_LEG_HIP_YAW`               | -2.7576 to 2.7576           |
| `9`       | `R_LEG_KNEE`                  | -0.087267 to 2.8798         |
| `10`      | `R_LEG_ANKLE_PITCH`           | -0.87267 to 0.5236          |
| `11`      | `R_LEG_ANKLE_ROLL`            | -0.2618 to 0.2618           |
| `12`      | `WAIST_YAW`                   | -2.618 to 2.618             |
| `13`      | `WAIST_ROLL`                  | -0.52 to 0.52               |
| `14`      | `WAIST_PITCH`                 | -0.52 to 0.52               |
| `15`      | `L_SHOULDER_PITCH`            | -3.0892 to 2.6704           |
| `16`      | `L_SHOULDER_ROLL`             | -1.5882 to 2.2515           |
| `17`      | `L_SHOULDER_YAW`              | -2.618 to 2.618             |
| `18`      | `L_ELBOW`                     | -1.0472 to 2.0944           |
| `19`      | `L_WRIST_ROLL`                | -1.972222054 to 1.972222054 |
| `20`      | `L_WRIST_PITCH`               | -1.614429558 to 1.614429558 |
| `21`      | `L_WRIST_YAW`                 | -1.614429558 to 1.614429558 |
| `22`      | `R_SHOULDER_PITCH`            | -3.0892 to 2.6704           |
| `23`      | `R_SHOULDER_ROLL`             | -2.2515 to 1.5882           |
| `24`      | `R_SHOULDER_YAW`              | -2.618 to 2.618             |
| `25`      | `R_ELBOW`                     | -1.0472 to 2.0944           |
| `26`      | `R_WRIST_ROLL`                | -1.972222054 to 1.972222054 |
| `27`      | `R_WRIST_PITCH`               | -1.614429558 to 1.614429558 |
| `28`      | `R_WRIST_YAW`                 | -1.614429558 to 1.614429558 |
| `29`      | `HEAD_PITCH`                  | -0.43633 to 0.62832         |
| `30`      | `HEAD_YAW`                    | -2.0071 to 2.0071           |

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

### External runtime power is not a verified pinout <a href="#external-runtime-power-is-not-a-verified-pinout" id="external-runtime-power-is-not-a-verified-pinout"></a>

G1+ advertises continuous external power/charging, and its original figure identifies a rear external input at DC 54.6 V, ≤7.4 A. The specification table separately lists a 54 V / 5 A charger. These labels do not establish the same adapter, mating connector, polarity, current-limiting behavior, grounding, insertion sequence, permissible simultaneous battery state or a firmware interlock. **Do not connect a bench supply or reuse base-G1 charging instructions.** Obtain the exact G1+ user and battery/power manual, approved adapter part number/nameplate and wiring before energizing either interface. [G1+ official page and feature figure](https://www.unitree.com/G1pl/)

A 13-series pack count is not a published safe nominal voltage or user-accessible GPIO level. No verified peripheral output budget, connector orientation, CAN/serial bus map, user Ethernet port/subnet, mounting torque or protective-stand rating was read for G1+. Port and charging work remains blocked. The folded dimensions describe an envelope; they do not authorize physically folding powered joints or using a G1 packing posture.

### Match the option set mechanically and logically <a href="#match-the-option-set-mechanically-and-logically" id="match-the-option-set-mechanically-and-logically"></a>

G1+ base body arithmetic is 12 leg + 10 arm + 1 waist + 2 head = **25 axes**. An EDU configuration can add waist, wrist and hand axes. The manufacturer's 25–45 range therefore cannot be converted into one default “45-joint G1+ EDU.” Retain the purchased option list, joint names, active axes, hand model, sensor/compute options and their documentation as one configuration record. This arithmetic is engineering interpretation of the published rows, not a delivered motor-ID map. [G1+ DoF table](https://www.unitree.com/G1pl/)

No G1+-specific startup posture, battery installation sequence, remote pairing or stop/recovery procedure was observed in the exact-model documentation reviewed here. The base G1 manuals and H2 emergency-stop manual are **not established as applicable**. Keep G1+ disconnected for this guide's first result. Before later power, obtain exact G1+ commissioning/stop instructions and match them to the delivered firmware and controller revision; do not assume a remote button provides a braking hold in custom low-level mode.

### Exact G1+ external ports and internal debug connector <a href="#exact-g1-external-ports-and-internal-debug-connector" id="exact-g1-external-ports-and-internal-debug-connector"></a>

The [original G1+ top-interface drawing](https://doc-cdn.unitree.com/static/2026/10/19/1d28063507704912932f974790bbac44_1793x1430.png) was visually inspected. It describes the EDU illustrated interface configuration:

| Drawing number | Interface and published role             |
| -------------- | ---------------------------------------- |
| `1`            | Type-C USB3 host plus DP1.4              |
| `2`            | Type-C USB3 host,5 V/2 A output          |
| `3`            | Four MMCX connections for GMSL2 cameras  |
| `4`, `5`       | XT30UPB-F12 V/10 A and 24 V/10 A outputs |
| `6`            | XT30UPB-F direct battery output, `VBAT`  |
| `7`            | Two Gigabit Ethernet ports               |

These are accessory outputs and communication roles, not charge inputs. The chapter does not establish every mating pin's polarity, VBAT current allowance, inrush or aggregate peripheral budget. **H2's500 W budget and connector polarities do not transfer to G1+.** The specific battery/charger and external-power rules below remain separate. [Exact hardware chapter](https://doc-cdn.unitree.com/39/1623/en/39_1623_en).

The [original rear debug drawing](https://doc-cdn.unitree.com/static/2026/11/9/0af4d3fd83cc40abbdd5a8e4cc1aca75_3179x1801.png) identifies an internal **GH1.25 eight-pin** interface, not a standard external RJ45 receptacle. Its pin1–8 table is `0P,0N,1P,1N,2P,2N,3P,3N`, mapped to orange-white/orange/green-white/green/blue-white/blue/brown-white/brown wires. This is the custom internal connector-to-wire mapping; it is **not standard RJ45 contact numbering or an instruction to crimp a cable**. PC1 remains reserved. Opening the back panel is not the default developer connection procedure; use the designated external port and supplied harness.

The developer PC2 reference is Orin NX16 GB/2 TB at **`192.168.123.164`**, with initial `unitree` / `123` in that image. The table's Intel-specific graphics/accelerator attributes mixed into an Arm module description are not accepted as verified NX hardware features. Confirm actual fitted compute, OS/image and network record. A generic `.161` connectivity target is not PC2 login. The source describes head MID360 with 360°×59° FOV; copied D435i captions and 23/29-DoF frame figures do not establish the exact G1+ camera or articulated-head calibration.

### Mounting-source geometry and useful limits of the drawings <a href="#mounting-source-geometry-and-useful-limits-of-the-drawings" id="mounting-source-geometry-and-useful-limits-of-the-drawings"></a>

The [G1+ front figure](https://doc-cdn.unitree.com/static/2026/10/19/3e94aa0364354690a2f0b757f8e6522e_1535x2120.png) and [rear figure](https://doc-cdn.unitree.com/static/2026/10/19/a99c35fb21bf4f7dbe5bef5a5daf074f_1534x2120.png) were visually checked. The front marks4-M6, upper spacing100.0 mm, lower64.5 mm and vertical179.5 mm; the rear marks4-M6, upper162.8 mm, lower120.8 mm and vertical155.8 mm. These are the depicted source geometry, not a structural load, lift attachment or torque specification. Match the delivered covers/revision and obtain usable engagement, fastener torque, accessory mass/moment limits and actual3D surfaces before designing a bracket. Preserve head motion, perception FOV, cooling and cable clearance. No older G1 drawing is silently substituted.

### G1+-specific external power and voice peripherals <a href="#g1-specific-external-power-and-voice-peripherals" id="g1-specific-external-power-and-voice-peripherals"></a>

The exact-model external-power chapter gives the order **install the battery → power on → connect the approved external charging module**. The module has limited current capability and cannot replace the pack for arbitrary all-motor demand. Before removing a pack while external power remains connected, the source requires **damping plus the approved supported posture**. A parenthetical squat/suspension example is not proof that every squat mode is damping or self-supporting. This chapter does not authorize live swapping on another model, an improvised supply or unverified module polarity/current. Its module identity/rating still must match the actual unit. The earlier product-figure DC54.6 V/≤7.4 A annotation and 54 V/5 A charger table are retained as separate source facts, not merged into one universal charging setting. [External-power chapter](https://doc-cdn.unitree.com/39/1669/en/39_1669_en), [original connection figure](https://doc-cdn.unitree.com/static/2026/10/26/03194615ac5848ba9d1e58ad8fe7f9b6_308x542.png).

The exact voice-interaction chapter uses **Unitree Explore → Settings → Audio Settings**, enabling the built-in/wireless microphone and restarting as instructed. The wake phrase is **笨笨同学** (`Benben Tongxue`). Removing the wireless transmitter from its case initiates pairing; fast blue flashing indicates failed pairing and the source describes replacing/retrying it. It defaults muted: hold for solid-blue recording, release for red-flashing mute. Confirm the actual fitted accessory/service. Voice activation is a state change and is excluded from the passive/offline first result; no cloud/privacy behavior was independently audited. [Voice interaction](https://doc-cdn.unitree.com/39/1668/en/39_1668_en).

### The inspected31-joint URDF and moving sensor frames <a href="#the-inspected31-joint-urdf-and-moving-sensor-frames" id="the-inspected31-joint-urdf-and-moving-sensor-frames"></a>

The actual [pinned `g1_pl.urdf`](https://github.com/unitreerobotics/unitree_ros/blob/157ff950351e5f535e03c5d85a16b7d594b3dbcc/robots/g1_description/g1_pl.urdf) is now read: SHA-256 **`9fea497eaf21f84d9fb1c1c713a0b5e486a9ef3391b305be6d81f94097927836`**, robot name `g1_pl`, **31 revolute plus 9 fixed joints**. It represents three waist axes, seven axes per arm and two neck axes; its fixed rubber-hand geometry does not model fourteen optional hand actuators. XML ordering is not DDS ordering: neck joints occur before arms in the file, so do not enumerate transport IDs by XML position.

| Model transform                          | URDF origin / role                                                  |
| ---------------------------------------- | ------------------------------------------------------------------- |
| `torso_link → head_base_link`            | xyz `0.01356,0.044798,0.29421` m, zero RPY                          |
| Neck pitch                               | axisY, origin `0,−0.0195,0` m, limits−0.43633..0.62832 rad          |
| Neck yaw                                 | axisZ, origin `0,−0.0253,0.08285` m, limits±2.0071 rad              |
| `head_link → camera_left_reference_link` | xyz `0.049922,0.028719,0.072513` m; RPY `0,0.790634151153431,0` rad |
| `head_link → lidar_reference_link`       | xyz `−0.012746,0.000328,0.054352` m; RPY `π,0,0` rad                |
| Torso IMU fixed frame                    | xyz `−0.03959,−0.00224,0.14792` m                                   |
| Pelvis IMU fixed frame                   | xyz `0.04525,0,−0.08339` m                                          |

Compose the actual torso/waist/neck pose chain to express camera/LiDAR data in the robot/world frame. A fixed transform from an older headless G1 cannot represent a moving G1+ neck. These are **model-reference transforms**, not per-unit camera calibration or measured extrinsics. URDF velocity/effort values are model parameters, not approved live gains, target speeds or contact-force limits; the head API's≈1 rad/s trajectory behavior is a different layer. Mesh dependencies were identified but not downloaded/rendered or simulator-validated. Reading XML does not establish a functioning G1+ Gazebo controller or model-to-delivered-unit equivalence.

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### What is actually supported by the reviewed evidence <a href="#what-is-actually-supported-by-the-reviewed-evidence" id="what-is-actually-supported-by-the-reviewed-evidence"></a>

The pinned `unitree_ros` README explicitly lists G1+ as `robots/g1_description/g1_pl.urdf`, with **31 actuated joints** in its model table. It explains that G1+ is a URDF variant inside `g1_description`. The product table, by comparison, spans 25–45 depending on edition and options. These statements describe different scopes: a specific model asset and a product range. Neither proves that the purchased unit has 31 active motors. [Pinned model catalog, commit `157ff950351e5f535e03c5d85a16b7d594b3dbcc`](https://github.com/unitreerobotics/unitree_ros/blob/157ff950351e5f535e03c5d85a16b7d594b3dbcc/README.md)

The exact pinned URDF download has now succeeded and its XML joints, limits, fixed-frame transforms and mesh references have been inspected as source data. The 31-revolute/9-fixed model findings are detailed below. Mesh files, a complete simulator/controller setup, delivered calibration and model-to-unit equivalence were not validated. The README limits its complete Gazebo controller setups to specific quadrupeds and does not establish a G1+ locomotion controller.

| Resource / claim                        | Observed state                                                                                  | Correct use                                                                                  |
| --------------------------------------- | ----------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| G1+ developer entitlement               | Product EDU column says Yes; base slash                                                         | Identify edition, then obtain exact development documentation                                |
| G1+ description asset                   | Exact pinned XML read; 31 revolute plus 9 fixed joints; full-body option scope                  | Inspected model reference; actual unit/configuration still needs qualification               |
| C++ SDK2                                | Commit `b7fec6020eb93d4c059a6edf19905e12a75a8d3d`; file tree has no explicitly named G1+ target | No exact G1+ hardware support asserted                                                       |
| Python SDK2                             | Commit `814556d15970dd2ecf1c9984e845ca02ab07e206`; file tree has no explicitly named G1+ target | G1 examples do not become G1+ examples                                                       |
| G1/G1 EDU examples                      | Related-model software exists                                                                   | Portal HG and exact-model head facts read; pinned/delivered compatibility conflicts retained |
| Firmware/image, transport, OS/toolchain | No exact G1+ compatibility matrix read                                                          | Install/build, ROS/DDS and connected tests remain deferred                                   |

The absence of a named path in those pinned trees is a bounded finding, not proof that Unitree never supports G1+. The now-read portal adds exact G1+ hardware/head information, mixed with legacy G1 chapters; a matching release/firmware contract is still needed. The required answer must name model, edition, SDK commit/package, firmware range, topic/schema, active joint map and stop/ownership behavior together. No such complete pairing was verified here.

### G1+ HG transport, configuration and separate hand messages <a href="#g1-hg-transport-configuration-and-separate-hand-messages" id="g1-hg-transport-configuration-and-separate-hand-messages"></a>

The assigned portal uses HG `LowState_`/`LowCmd_` body messages with 35 motor entries. `mode_pr=0` is virtual PR; `1` is direct AB for the coupled ankle/waist mechanisms. **G1+ ankle pitch is 4/10, roll5/11**, opposite H2's roll4/10/pitch5/11. Under AB, pitch maps to B and roll to A; waist roll13 maps to A and pitch14 to B. PR joint limits are not interchangeable with direct actuator limits. [Joint sequence](https://doc-cdn.unitree.com/39/1641/en/39_1641_en).

The portal's Basic Services sketch omits the pinned HG state's `version[2]`, shows `MotorCmd.reserve[3]` instead of the pinned single element and mixes in GO raw-motor fields absent from pinned HG. **Use the actual generated bindings**, not a composite decoder copied from the portal. IMU quaternion is `w,x,y,z`; body motor position/velocity/acceleration and torque have their specific types/units. Topic names and plausible numbers do not prove a serialization or firmware match. No complete exact G1+/edition/firmware/SDK pairing is established by these conflicting sketches. [Basic services](https://doc-cdn.unitree.com/39/1645/en/39_1645_en), [pinned HG source](https://github.com/unitreerobotics/unitree_sdk2/tree/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/hg).

Dex3 uses separate HG `HandCmd_`/`HandState_` on left/right hand topics. The **currently visible** sequence is thumb0/1/2, **middle3/4, index5/6**. An older commented table reverses middle/index; it is not the accepted current map. Hand state contains motor/IMU/pressure-sensor sequences and its own power voltage/current. `PressSensorState` has pressure\[12] and temperature\[12] **per pad**; this is not twelve hand joints. Nine sensor arrays in the hardware table and seven actuators are separate counts. [Current hand sequence](https://doc-cdn.unitree.com/39/1641/en/39_1641_en), [hand message fields](https://doc-cdn.unitree.com/39/1645/en/39_1645_en).

### Shared DDS/RPC APIs and installed-version checks <a href="#shared-ddsrpc-apis-and-installed-version-checks" id="shared-ddsrpc-apis-and-installed-version-checks"></a>

The actual pinned `ChannelFactory::Init(domain,interface)` accepts **two arguments**. The portal's third shared-memory argument is not available at that pin; the subscriber's receive path is `CreateRecvChannel`, despite send-creator prose; `GetServerApiVersion()` returns a string by value, despite the reference signature in the chapter. Callback queues can keep slow work off DDS but retain buffered age. Last-data time is monotonic microseconds since startup, not wall-clock acquisition time. RPC timeout takes seconds and a lease wait may block. Contradictory `rt/lf` hand captions do not establish actual stream rates. [DDS service](https://doc-cdn.unitree.com/39/1643/en/39_1643_en), [pinned factory](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/channel/channel_factory.hpp), [pinned client](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/client/client.hpp).

The SDK/architecture chapters distinguish continuous DDS publish/subscribe from request/response matched by UUID. Cloud/app transport is described as authorized MQTT monitoring/OTA/signaling, HTTP binding, BLE setup/authentication, WebRTC media/state/control and STUN/TURN connectivity or relay. These are source descriptions, not an independent privacy audit. The older SDK Overview's “GST not yet supported” text must be read alongside later service/version chapters rather than treated as universal current hardware behavior. [SDK overview](https://doc-cdn.unitree.com/39/1636/en/39_1636_en), [architecture](https://doc-cdn.unitree.com/39/1637/en/39_1637_en).

Quick Development names Linux/Ubuntu20.04, host `.123.99`/`.222`, the actual host interface and a `.161` connectivity target; the developer PC2 remains `.164` where delivered. Its G1 ankle-swing executable is **active legacy G1 code**, not a verified G1+ first run. A source checkout and globally installed SDK may differ; match commit, headers, linked library and generated binary. Native SDK2 does not require ROS. The ROS routine's Foxy/Humble/CycloneDDS0.10.2 and generic message-package text need actual HG/package/version qualification. The HelloWorld DDS routine teaches synthetic publishing and subscriber close/reinitialization, not physical G1+ compatibility. Separate simulator discovery from live networks/domains before any later simulator workflow. No simulator or SDK was run here. [Quick development](https://doc-cdn.unitree.com/39/1639/en/39_1639_en), [ROS routine](https://doc-cdn.unitree.com/39/1658/en/39_1658_en), [DDS routine](https://doc-cdn.unitree.com/39/1659/en/39_1659_en).

### Head API: exact portal contract, absent from the pinned wrapper <a href="#head-api-exact-portal-contract-absent-from-the-pinned-wrapper" id="head-api-exact-portal-contract-absent-from-the-pinned-wrapper"></a>

The exact G1+ head chapter documents `g1::LocoClient::SetHead(pitch,yaw)`, service `sport`, API **`7113`**. Both inputs are required numeric radians. Pitch is−0.4363..+0.6283, positive forward; yaw−2..+2 (about±114°). Missing/wrong-type fields return `3204`; out-of-range numeric values are **clipped without an error**. Return0 starts a nonblocking smooth motion at about 1 rad/s and holds the target until a new request or damping. Damping removes head torque and ignores the target; leaving damping automatically returns the head toward zero. Those transitions can move hardware and require the built-in service, not Develop ownership. [Exact head chapter](https://doc-cdn.unitree.com/39/1660/en/39_1660_en).

**SDK version gate:** actual `b7fec602` `g1_loco_client.hpp`/`g1_loco_api.hpp` do **not** contain `SetHead`/`7113`, and the pinned tree does not contain the chapter's head-control example. Therefore this guide gives the portal contract as a newer interface reference, **not a compile recipe using that pinned SDK**. Obtain a matching wrapper/server/firmware release before use; do not invent a helper method or silently send a raw command as a first result. Mechanical head limits and API clipping intervals are also distinct source values.

### Locomotion, controller switching and topic-specific blending <a href="#locomotion-controller-switching-and-topic-specific-blending" id="locomotion-controller-switching-and-topic-specific-blending"></a>

The assigned sport chapter describes G1 `g1::LocoClient` with zero torque0, damp1, squat2, sit3, stand-up4 and start500/501 for waist variants. It also lists balance-squat706, lie/stand702 and running801→802 after `ai_sport8.6.x`. These are legacy service/feature relationships, not universal G1+ minimum firmware or model identification. Source speed-mode0–3 maxima1/2/2.7/3 m/s are **G1 service claims**, not verified G1+ speed ratings. The pinned default `Move` lasts one second; its explicit continuous path uses a long duration. `SwitchMoveMode` and `ContinuousGait` are separate actual functions despite a portal prototype typo. [Sport service](https://doc-cdn.unitree.com/39/1646/en/39_1646_en).

`UserCtrl` API `7110` routes **all-motor** commands through `rt/user_lowcmd` and requires the documented standard-standing transitions; `InternalCtrl` API `7111` selects actual `LAST/PASSIVE/WALKRUN` enum0/1/2. These are controller-ownership writes and are excluded from the first observation. The HG high-level `SportModeState_` with `fsm_id,mode,task_id,time` is **not** the GO odometry `SportModeState_` with position/velocity fields. Namespace and service matter. Its firmware 1.5.1 state feature and static/dynamic mode restrictions are not a complete G1+ compatibility matrix.

The legacy G1 arm-blending example publishes HG `LowCmd_` on `rt/arm_sdk` and puts weight in **slot 29.q**. On G1+'s ordinary body `rt/lowcmd`, slot 29 is head pitch. These are different **topic semantics**, not proof that the topics physically collide; they are also not permission to reuse a29-DoF arm example on a31-joint head-equipped unit. Confirm the server's exact arm/head/optional-wrist contract first. Its five-second pose/weight ramps and two-second blend-out actively move hardware. [Arm routine](https://doc-cdn.unitree.com/39/1654/en/39_1654_en).

The Motion Switcher article's title/path is inconsistent and its prose includes Go2 standard/wheeled labels. `CheckMode` is a query; `SelectMode` and `ReleaseMode` change ownership. The model-form result is not accepted as a G1+ physical ID from that copied table. The pinned shared MotionSwitcher header is actually under `unitree/robot/b2/motion_switcher/motion_switcher_client.hpp`; that path/namespace is real, while the copied Go2 form labels still do not qualify G1+ hardware. Errors `7001,7002,7004..7009` distinguish parameter, busy, unsupported, internal, check, switch, release and custom-configuration failures. **No release or service-disable call belongs in the first state check.** [Motion Switcher](https://doc-cdn.unitree.com/39/1651/en/39_1651_en).

The RPC keyboard routine defaults to loopback `lo` and processes a `std::map` in lexical key order rather than argument order; empty-value front/back access is unsafe. Its historical `sport` versus `loco` distinction around `ai_sport8.2` is a service-version statement, not a blanket G1+ minimum. Queries and setters are separate, and a copied key table does not guarantee a handler exists at the pinned source. Treat the routine as functional examples, not a ready action sequencer or external-interface selection. [RPC routine](https://doc-cdn.unitree.com/39/1653/en/39_1653_en).

### Preset arm actions and the internally wired hand-SDK route <a href="#preset-arm-actions-and-the-internally-wired-hand-sdk-route" id="preset-arm-actions-and-the-internally-wired-hand-sdk-route"></a>

The actual pinned preset-action class is **`G1ArmActionClient`**, whereas the portal sometimes calls it `ArmAction`. `ExecuteAction(int)` selects a preset and the string overload uses a case-sensitive taught name. `GetActionList` returns an integer status with output data containing supported actions/durations/requirements; inspect success and the delivered list rather than assuming every pictured gesture exists. `StopCustomAction` is itself an active return-motion request. The portal's blocking/nonblocking labels do not prove physical completion: observe `rt/arm/action/state` fields `holding,id,name` with appropriate freshness. Source comments mention a20 s hold and custom action ID100, not a universal timing guarantee. [Arm actions](https://doc-cdn.unitree.com/39/1655/en/39_1655_en), [pinned action client](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/g1/arm/g1_arm_action_client.hpp).

Action errors `7400` occupied,`7401` held,`7402` missing and `7404` wrong FSM require different diagnosis. The documented held-state recovery action99 or same-ID behavior is a control action, not an automatic diagnostic retry. The example that disables a service before custom arm control changes ownership; it is not a prerequisite for a passive state reader.

The internal hand-SDK interface is **GO `MotorCmds_` on `rt/hand_sdk` with four command slots**, for documented Dex2-5/Dex1-1 routes. It is neither HG Dex3's seven-motor state nor H1 Inspire's six actuators per side. Encode **`weight * 100` as an integer 0–100 in `cmds[0].mode`** and decode by dividing by 100; other mode bytes are unused. It blends `kp,kd,q,dq,tau` with the built-in `ai_sport` command. Positive **`tau` closes**, negative opens; this is not a universal position-sign convention. When the user command differs from the `ai_sport` default, an abrupt weight change from **0 to 1 can produce abrupt hand movement**. Damping blocks forwarding, and leaving damping requires resetting the weight. If the user process stops publishing, the documented timeout fallback returns to **`ai_sport`'s default hand behavior**; it does not establish a stop, torque-off or a maintained grip/pose. The numerical timeout threshold is not disclosed. [Hand interface and Notes](https://doc-cdn.unitree.com/39/1656/en/39_1656_en).

The [actual pinned hand example](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/g1/high_level/g1_hand_sdk_example.cpp) does exist: it creates a publisher, sets full weight and alternates torque forever. That establishes source availability, **not a passive or qualified G1+ hand test**. Do not execute it to identify a tool or guess force limits.

### Odometry, LiDAR frames and time synchronization <a href="#odometry-lidar-frames-and-time-synchronization" id="odometry-lidar-frames-and-time-synchronization"></a>

The assigned G1 odometry chapter requires the built-in controller and **StateEstimator≥1.0.0.1 for that feature**, not H2's2.1.0.12 or a universal G1+ minimum. It uses GO `SportModeState_` on `rt/odommodestate`/`rt/lf/odommodestate`, vendor-reported500/20 Hz. Position metres and velocity m/s are world-frame quantities; the initialized ground-projection frame has+Xforward,+Yleft,+Zup, quaternion `w,x,y,z`, RPYradians and yaw speedrad/s. Develop mode disables that high-level service. Verify reset/frame/clock history before sensor fusion; the copied common-table `IMUState_` label is not the correct odometry decoder. [Odometry](https://doc-cdn.unitree.com/39/1647/en/39_1647_en).

The LiDAR chapter gives `LidarDriver≥1.0.0.5` for its service and says G1 produced afterApril2026 may use **MID360 s**, needing matching Livox SDK2/driver support. That does not prove every delivered G1+ has that sensor. It lists `rt/utlidar/cloud_livox_mid360` (`PointCloud2_`,10 Hz,`livox_frame`) and `rt/utlidar/imu_livox_mid360` (`Imu_`,200 Hz) as source claims, not observed rates. [LiDAR service](https://doc-cdn.unitree.com/39/1649/en/39_1649_en).

The older G1 chapter gives an IMU/LiDAR translation `(0.011,0.02329,−0.04412)` m without a sufficiently clear transform direction, and a fixed base offset `(0,0,−0.47618)` m with inverted mounting/pitch−2.3°. These are retained as **legacy source geometry only**, not a constant G1+ TF. The inspected G1+ URDF above has a moving neck and explicit sensor-reference frames; real calibration and pose-dependent transforms must match the delivered assembly.

The time-sync chapter describes NTP from PC1 `.123.161` for **G1 firmware>1.5.1 as that feature's condition**. Wi-Fi synchronization may step the clock, so a received wall timestamp can jump even when local monotonic age is continuous. Chrony and systemd-timesyncd are alternative owners, not services to configure concurrently. The source's Chrony `iburst/prefer`, initial `makestep`, RTC synchronization, sources/tracking queries and polling controls describe a configuration workflow, not measured NTP/PTP accuracy. Its `-F0` workaround disables Chrony's seccomp filtering and is **not a normal prerequisite**; the printed `unmusk` typo is not a valid command. No clock service was changed here. [Time sync](https://doc-cdn.unitree.com/39/1652/en/39_1652_en).

### SLAM mapping, localization and task feedback <a href="#slam-mapping-localization-and-task-feedback" id="slam-mapping-localization-and-task-feedback"></a>

The assigned service is **`slam_operate`, API version `1.0.0.1`**, requiring `unitree_slam` and `lidar_driver` enabled and no simultaneous app navigation owner. The reference is a static, feature-rich, flat indoor environment with X/Y extent<45 m, intended for research rather than an industrial navigation guarantee. The documented per-goal straight-line target distance is ≤10 m. Separately, the radar sensing/FOV condition requires a **minimum obstacle height of 50 cm**; it establishes neither horizontal standoff nor traversable height or underbody clearance. Violent motion, loose sensors and an incorrect initial pose degrade the result; a moving G1+ head additionally requires correctly composed sensor transforms. Reference PC2 `.164`/LiDAR `.120` addresses are not an instruction to overwrite a newer sensor network. [SLAM service](https://doc-cdn.unitree.com/39/1650/en/39_1650_en).

| API            | Documented functional request                                            |
| -------------- | ------------------------------------------------------------------------ |
| `1801`         | Start indoor mapping                                                     |
| `1802`         | Finish/save map to the specified PCD path                                |
| `1804`         | Initialize localization with map address,xyz position andxyzw quaternion |
| `1102`         | Target-pose navigation, documented mode1                                 |
| `1201`, `1202` | Pause / resume navigation                                                |
| `1901`         | Close SLAM                                                               |

Check the **RPC return code** separately from the returned JSON response string. Parse that string and inspect its **top-level `succeed`, `errorCode` and `info`**, alongside the separate nested `data` payload; the documented success path is `response["succeed"]`, not `response["data"]["succeed"]`. A C++ variable named `data` can hold the entire response string and does not define a nested JSON field. JSON comments,`XXX` placeholders and trailing commas in examples are not valid JSON payloads. A success return is not physical arrival; use current task feedback. Mapping point cloud/odometry topics are `rt/unitree/slam_mapping/points` / `rt/unitree/slam_mapping/odom`; relocation topics are `rt/unitree/slam_relocation/points` / `rt/unitree/slam_relocation/odom`; global map `rt/unitree/slam_relocation/global_map` is sent only once after relocation starts. Clouds use `PointCloud2_`, odometry uses `Odometry_`. Late subscribers may miss the single map publication.

`rt/slam_info` /`String_` separates `robot_data` temperatures/current(mA)/battery voltage(mV)/SOC/CPU/memory/frequency(MHz),`pos_info`, mapping/map-file information and `ctrl_info` target/start/pose/state/velocity/obstacle/time/progress. `rt/slam_key_info` carries task-result/arrival feedback. The map frame is described from the MID360 IMU with Xforward/Zup; it is not automatically the robot base frame. Preserve request/task identity, timestamps and frame provenance in a data collector.

The linked navigation archive was inspected as source only. Its keyboard application starts/saves maps, initializes localization, appends/executed waypoints and pauses/resumes. Critically, its destructor calls close-SLAM API `1901`, so even exiting that program changes robot service state. Detached task threads, unbounded arrival waits, unchecked RPC results/JSON and example save paths are not a production recovery procedure. It is excluded from the first result. [Original navigation example archive](https://oss-global-cdn.unitree.com/static/dd442abf94ec44f599095cb15c3e298b.zip).

### Local audio service and historical training resources <a href="#local-audio-service-and-historical-training-resources" id="local-audio-service-and-historical-training-resources"></a>

The assigned VUI chapter requires `VuiService≥2.0.3.8` and module≥2.0.0.3 for its features. It describes six microphones at 20 mm spacing and a10 W speaker, whereas exact G1+ About lists **two 10 W speakers**; do not replace the hardware count with reused prose. Introductory Chinese-only TTS conflicts with role0Chinese/1English tables/examples. Confirm service/region before promising English. Volume0–100, RGB0–255 with LED calls>200 ms apart, mono16kHz/16-bit PCM, same-stream-ID cache continuation/different-ID interruption and application-scoped playback stop are distinct controls. [VUI service](https://doc-cdn.unitree.com/39/1648/en/39_1648_en).

`rt/audio_msg` /`String_` carries ASR sequence/time/text/angle0–180/speaker/emotion/confidence/language/final flag or playback0/1 state. Validate real messages because sample commas/types are inconsistent; offline non-streaming recognition is default. The example receives microphone PCM at `239.168.123.161:5555`, but also changes volume/LEDs, speaks and loops recording. It is not a passive robot-health check or a synchronized sensor dataset. The exact newer microphone workflow belongs to the G1+ Voice chapter above.

The RL chapter's task is **`g1`**, not a G1+25/31/45 configuration. IsaacGymPreview4, driver525, Python3.8, Torch1.10/cu113, NumPy1.23.5 andrsl\_rl1.0.2 are a historical source environment, not a current install recommendation or proof of head-equipped G1+ policy compatibility. Preserve observation/action order, model geometry and controller ownership before any separately authorized training/sim-to-real work. No training, simulator, model build or policy deployment occurred. [RL routine](https://doc-cdn.unitree.com/39/1657/en/39_1657_en).

### Pinned learning resources: workflow reference, not a live deployment recipe <a href="#pinned-learning-resources-workflow-reference-not-a-live-deployment-recipe" id="pinned-learning-resources-workflow-reference-not-a-live-deployment-recipe"></a>

The actual [Unitree RL Gym README at commit 276801e46c5d433564f24658bac64f254b7d2d4b](https://github.com/unitreerobotics/unitree_rl_gym/blob/276801e46c5d433564f24658bac64f254b7d2d4b/README.md) names tasks `go2`, `g1`, `h1`, `h1_2` and describes **Train → Play → Sim2Sim → Sim2Real**. Train options distinguish checkpoint/run selection, parallel environment count, seed, iterations and simulation/RL devices. Play exports MLP `policy_1.pt` or recurrent `policy_lstm_1.pt` under the experiment's exported policies directory. MuJoCo uses a selected YAML configuration and `policy_path`; physical deployment uses a different configuration and explicit robot-facing interface. Those are different stages, not interchangeable commands. The G1 C++ deployment example additionally depends on LibTorch. These are source/resource facts only: no environment, simulator, policy or hardware code was installed/run, and the named `g1` task does not qualify G1+ or H2-X.

## Getting started <a href="#getting-started" id="getting-started"></a>

### Prerequisites and model qualification <a href="#prerequisites-and-model-qualification" id="prerequisites-and-model-qualification"></a>

Keep G1+ disconnected. Use a browser for source inspection and, optionally, Python 3 for the standalone synthetic example. No exact G1+ live API/firmware pairing is established here. Base G1 software must not be substituted for that missing contract.

### First working result: distinguish a model asset from a hardware target <a href="#first-working-result-distinguish-a-model-asset-from-a-hardware-target" id="first-working-result-distinguish-a-model-asset-from-a-hardware-target"></a>

1. Open the [official G1+ product table](https://www.unitree.com/G1pl/). Record G1+ base 25 DoF versus G1+ EDU 25–45 DoF, and the separate secondary-development entries. Keep the `+` in the identity.
2. Open the [official model catalog at commit 157ff950](https://github.com/unitreerobotics/unitree_ros/blob/157ff950351e5f535e03c5d85a16b7d594b3dbcc/README.md). Find the G1+ row, `g1_pl.urdf`, its 31-joint model scope and the explanation that it is a variant inside `g1_description`. Also inspect the [actual pinned URDF](https://github.com/unitreerobotics/unitree_ros/blob/157ff950351e5f535e03c5d85a16b7d594b3dbcc/robots/g1_description/g1_pl.urdf): it has 31 revolute and 9 fixed joints, including the articulated head; XML order is not the DDS index map.
3. Inspect the [C++ SDK2 tree at commit b7fec602](https://github.com/unitreerobotics/unitree_sdk2/tree/b7fec6020eb93d4c059a6edf19905e12a75a8d3d) and [Python SDK2 tree at commit 814556d1](https://github.com/unitreerobotics/unitree_sdk2_python/tree/814556d15970dd2ecf1c9984e845ca02ab07e206). Look for an explicitly documented G1+ target and firmware contract. G1 examples alone are insufficient; a missing named path does not prove global non-support.
4. Record the product's option range, the specific model-catalog variant and the unresolved physical SDK/firmware mapping as three separate findings. Do not choose a 29- or 31-joint executable merely to fit a count.

**Expected result:** a note stating “G1+ base 25; EDU 25–45; inspected URDF 31 revolute plus 9 fixed joints; portal head API newer than pinned SDK; exact delivered firmware pairing unresolved.” The result is an explicit compatibility boundary, not an approved live target. Unavailable links leave that source check incomplete.

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

### The next physical milestone requires exact G1+ evidence <a href="#the-next-physical-milestone-requires-exact-g1-evidence" id="the-next-physical-milestone-requires-exact-g1-evidence"></a>

Resolve developer entitlement, purchased options, body/hand ID map, firmware/image, SDK target/schema, network settings and model-specific power/stop instructions before a later identity/state read. Use only an explicitly supported status API or subscriber, with no motion publisher or mode takeover. Require valid fresh data and label only verified axes. The generic synthetic values above do not establish a G1+ HG message schema or transport.

### Operating chapters filed under G1+ still need exact-model qualification <a href="#operating-chapters-filed-under-g1-still-need-exact-model-qualification" id="operating-chapters-filed-under-g1-still-need-exact-model-qualification"></a>

The assigned Quick Start/Remote chapters explicitly show older **G1 23/29-DoF** photos, videos and controller revisions. Their seated and hanging routes use different combinations; seated/squat modes may have no balance, and a standing controller can make corrective steps. Sticker version gates<8.2/≥8.2 and later8.4.2.222/8.5/8.6 feature changes are source revision facts, not G1+ firmware minimums. They do not establish an exact G1+25/31-body-joint boot/stop/calibration procedure. Original videos/stickers are resource links, not watched/tested procedures here. [Assigned Quick Start](https://doc-cdn.unitree.com/39/1628/en/39_1628_en), [assigned remote](https://doc-cdn.unitree.com/39/1629/en/39_1629_en).

The legacy guide lists L2+R2Develop, L2+Yzero, L2+Bdamp, L2+UPready, L2+LEFTseat, L2+Xlie/stand and L2+Asquat/diagnostic-dependent actions, plus gait/gesture keys. **These are documented older-G1 functions, not instructions to press them on an unqualified G1+.** Several require holds or particular controller states. Its claim of damping in Debug does not override model-specific low-level ownership uncertainty or make a remote a hardware-stop circuit. The exact G1+ physical instructions remain a commissioning dependency.

The updated developer stand photo shows all four castors locked and an external shoulder-Ethernet connection, while surrounding text is reused G1 material. Secure the correct support and use the exact G1+ external port; opening the internal GH debug connector or launching an active ankle/arm/head example is not part of the offline first result. The built-in controller may keep writing zero-speed commands even at neutral appearance. [Developer setup](https://doc-cdn.unitree.com/39/1635/en/39_1635_en), [reused More Cases text](https://doc-cdn.unitree.com/39/1634/en/39_1634_en).

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

**A search finds G1 but not G1+. Is that sufficient?** No. Preserve the manufacturer `G1pl` identity and exact model/option scope. Base G1 store products and wiki pages are related references, not G1+ matches. This guide intentionally has null SKU/store URL until an exact listing is observed. [G1+ official page](https://www.unitree.com/G1pl/)

**The URDF catalog says 31 while the product says 25–45.** Treat 31 as one named description variant, not a correction to the product table or proof of your robot's axis count. Read the actual URDF and purchased BOM, identify fixed/active/transmission joints, and obtain the controller ID map. File contents were not verified here because the raw fetch timed out. [Pinned model catalog](https://github.com/unitreerobotics/unitree_ros/blob/157ff950351e5f535e03c5d85a16b7d594b3dbcc/README.md)

**Can I calculate absolute G1+ torque from the percentage upgrades?** No absolute rating or full test basis was supplied in the read upgrade panel. Keep the relative claim with its conditions; obtain exact actuator/body limits for planning. Never use the resulting arithmetic as a command bound. [Motor-upgrade panel](https://www.unitree.com/G1pl/)

**The rear input says 54.6 V but the charger table says 54 V. Which supply is correct?** They are different source labels for different interface roles. The reviewed evidence does not establish adapter interchangeability or pinout. Ask for exact approved G1+ power parts and instructions before connecting anything. [Original feature figure](https://www.unitree.com/images/32be40654390458795e906bb649c532c_2000x1346.png?x-oss-process=image/format,webp)

**Does tapping the head only record a sensor value?** The manufacturer feature says tapping can initiate dialogue and trigger motion. Do not probe tactile behavior on a powered, unqualified unit as a passive sensor test. Obtain the touch-event API and interaction-mode behavior first. [G1+ tactile panel](https://www.unitree.com/G1pl/)

**Can I use base G1 maintenance, calibration or emergency-stop instructions?** No applicability was verified. Obtain exact G1+ manuals, controller revision and firmware-specific recovery instructions. No maintenance disassembly, calibration or reset steps are invented in this guide.

### Diagnose schema, API and ownership mismatches before physical experiments <a href="#diagnose-schema-api-and-ownership-mismatches-before-physical-experiments" id="diagnose-schema-api-and-ownership-mismatches-before-physical-experiments"></a>

An unavailable head method at the pinned commit is expected from the source/version mismatch, not evidence that the head motor is defective. Preserve the portal API 7113 contract, exact installed server/package and mechanical configuration; obtain the matching wrapper before compiling an active application. Do not fabricate the method, bypass the service or use a low-level head slot to test it.

A body count25/31, a product option45, stale23/29table headings and 35 transport capacity must stay separate in logs and error reports. Reject a state decoder that only “looks plausible”; compare actual version fields, fixed-array capacities, namespace and mode with the delivered firmware contract. Do not enable unused waist/wrist slots or infer optional-hand state from body padding.

RPC `3001` is unknown; client `3102..3107` distinguish send failure, unregistered API, timeout, response mismatch, invalid response and invalid lease. Server `3202..3207` distinguish internal error, unimplemented API, bad parameters, rejected request, invalid lease and existing lease; server response-send failure `3201` is not returned to the client. Fault bitmasks, rejected motion requests, a stale stream and a physical stop trigger are different evidence. Preserve raw fields, API/version, controller owner, tick and local monotonic receive age; no automatic release, firmware update or calibration follows from a timeout. [DDS errors](https://doc-cdn.unitree.com/39/1643/en/39_1643_en).

For LiDAR/SLAM inconsistency, inspect actual sensor revision and active head transforms, driver/service versions, map/initial pose, changing environment and clock history before claiming a localization fault. A successful API response, single retained global map or static cached point cloud does not prove a current collision-free route. For audio, distinguish microphone mute/wake state, local service versus online features and actual format/stream ID before changing system services. The exact-model power, module identity, physical support and stop/isolation gaps remain material even after more article text becomes accessible.

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

| Resource                  | Model / purpose                                                                        | Link                                                                                                                                                              |
| ------------------------- | -------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| G1+ product page          | Exact G1+/G1+ EDU feature and specification table                                      | [Official G1+](https://www.unitree.com/G1pl/)                                                                                                                     |
| G1+ feature diagram       | Original manufacturer illustration; touch, vision, head axes and rear power annotation | [Original figure](https://www.unitree.com/images/32be40654390458795e906bb649c532c_2000x1346.png?x-oss-process=image/format,webp)                                  |
| Official model catalog    | Pinned README with explicit G1+ description reference; read                            | [Unitree ROS model table](https://github.com/unitreerobotics/unitree_ros/blob/157ff950351e5f535e03c5d85a16b7d594b3dbcc/README.md)                                 |
| Candidate G1+ URDF        | Exact pinned XML read; 31-body-joint option and reference frames inspected             | [g1\_pl.urdf at the pinned commit](https://github.com/unitreerobotics/unitree_ros/blob/157ff950351e5f535e03c5d85a16b7d594b3dbcc/robots/g1_description/g1_pl.urdf) |
| Developer document center | Obtain exact G1+ manual and firmware/SDK confirmation                                  | [Official support portal](https://support.unitree.com/main/en)                                                                                                    |

The 37 supplied developer records are now reviewed, including exact G1+ hardware, head, voice and external-power chapters. Exact G1+ user/battery/remote operating manuals, a complete electrical schematic, delivered-unit load/mounting approval, API/firmware compatibility matrix and qualified live state program remain unverified. No manual chapter coverage is claimed for those missing documents. The existing G1 English manuals do not fill those rows. See the separate [H2](https://www.unitree.com/H2/) and [H2-X](https://www.unitree.com/H2-X/) manufacturer specifications for other models; their hardware guidance does not apply here.

### Portal article and functional-section index <a href="#portal-article-and-functional-section-index" id="portal-article-and-functional-section-index"></a>

The following index covers the supplied exact collection, including empty navigation nodes. It points to original-English engineering interpretation above; it does not republish manual transcripts, SDK source bundles or unviewed media. A linked figure, video, CAD archive or driver package is a separate evidence boundary.

| Actual article                                                                                        | Applicability/read state       | Guide destination                                                                                                        |
| ----------------------------------------------------------------------------------------------------- | ------------------------------ | ------------------------------------------------------------------------------------------------------------------------ |
| [About G1+](https://doc-cdn.unitree.com/39/1623/en/39_1623_en)                                        | Read with model/version limits | [Interpretation and boundary](unitree-g1-plus.md#exact-g1-external-ports-and-internal-debug-connector)                   |
| [Operational Guidance](https://doc-cdn.unitree.com/39/1627/en/39_1627_en)                             | Index only                     | [Interpretation and boundary](unitree-g1-plus.md#downloads-and-technical-documents)                                      |
| [Quick Start](https://doc-cdn.unitree.com/39/1628/en/39_1628_en)                                      | Read with model/version limits | [Interpretation and boundary](unitree-g1-plus.md#operating-chapters-filed-under-g1-still-need-exact-model-qualification) |
| [Remote Control](https://doc-cdn.unitree.com/39/1629/en/39_1629_en)                                   | Read with model/version limits | [Interpretation and boundary](unitree-g1-plus.md#operating-chapters-filed-under-g1-still-need-exact-model-qualification) |
| [Voice Interaction](https://doc-cdn.unitree.com/39/1668/en/39_1668_en)                                | Read with model/version limits | [Interpretation and boundary](unitree-g1-plus.md#g1-specific-external-power-and-voice-peripherals)                       |
| [External Power Supply Guide](https://doc-cdn.unitree.com/39/1669/en/39_1669_en)                      | Read with model/version limits | [Interpretation and boundary](unitree-g1-plus.md#g1-specific-external-power-and-voice-peripherals)                       |
| [Application Development](https://doc-cdn.unitree.com/39/1630/en/39_1630_en)                          | Index only                     | [Interpretation and boundary](unitree-g1-plus.md#downloads-and-technical-documents)                                      |
| [SDK Overview](https://doc-cdn.unitree.com/39/1636/en/39_1636_en)                                     | Read with model/version limits | [Interpretation and boundary](unitree-g1-plus.md#shared-ddsrpc-apis-and-installed-version-checks)                        |
| [Architecture Description](https://doc-cdn.unitree.com/39/1637/en/39_1637_en)                         | Read with model/version limits | [Interpretation and boundary](unitree-g1-plus.md#shared-ddsrpc-apis-and-installed-version-checks)                        |
| [Get SDK](https://doc-cdn.unitree.com/39/1638/en/39_1638_en)                                          | Index only                     | [Interpretation and boundary](unitree-g1-plus.md#downloads-and-technical-documents)                                      |
| [Quick Development](https://doc-cdn.unitree.com/39/1639/en/39_1639_en)                                | Read with model/version limits | [Interpretation and boundary](unitree-g1-plus.md#shared-ddsrpc-apis-and-installed-version-checks)                        |
| [Services Interface](https://doc-cdn.unitree.com/39/1632/en/39_1632_en)                               | Index only                     | [Interpretation and boundary](unitree-g1-plus.md#downloads-and-technical-documents)                                      |
| [DDS Services Interface](https://doc-cdn.unitree.com/39/1643/en/39_1643_en)                           | Read with model/version limits | [Interpretation and boundary](unitree-g1-plus.md#shared-ddsrpc-apis-and-installed-version-checks)                        |
| [Robot State Client Interface](https://doc-cdn.unitree.com/39/1644/en/39_1644_en)                     | Index only                     | [Interpretation and boundary](unitree-g1-plus.md#downloads-and-technical-documents)                                      |
| [Odometer Service Interface](https://doc-cdn.unitree.com/39/1647/en/39_1647_en)                       | Read with model/version limits | [Interpretation and boundary](unitree-g1-plus.md#odometry-lidar-frames-and-time-synchronization)                         |
| [VuiClient Service Interface](https://doc-cdn.unitree.com/39/1648/en/39_1648_en)                      | Read with model/version limits | [Interpretation and boundary](unitree-g1-plus.md#local-audio-service-and-historical-training-resources)                  |
| [Lidar Services Interface](https://doc-cdn.unitree.com/39/1649/en/39_1649_en)                         | Read with model/version limits | [Interpretation and boundary](unitree-g1-plus.md#odometry-lidar-frames-and-time-synchronization)                         |
| [SLAM and Navigation Services Interface](https://doc-cdn.unitree.com/39/1650/en/39_1650_en)           | Read with model/version limits | [Interpretation and boundary](unitree-g1-plus.md#slam-mapping-localization-and-task-feedback)                            |
| [Time Sync Interface](https://doc-cdn.unitree.com/39/1652/en/39_1652_en)                              | Read with model/version limits | [Interpretation and boundary](unitree-g1-plus.md#odometry-lidar-frames-and-time-synchronization)                         |
| [Basic Motion Development](https://doc-cdn.unitree.com/39/1631/en/39_1631_en)                         | Index only                     | [Interpretation and boundary](unitree-g1-plus.md#downloads-and-technical-documents)                                      |
| [Joint Motor Sequence](https://doc-cdn.unitree.com/39/1641/en/39_1641_en)                             | Read with model/version limits | [Interpretation and boundary](unitree-g1-plus.md#g1-hg-transport-configuration-and-separate-hand-messages)               |
| [Basic Motion Routine](https://doc-cdn.unitree.com/39/1640/en/39_1640_en)                             | Read with model/version limits | [Interpretation and boundary](unitree-g1-plus.md#g1-hg-transport-configuration-and-separate-hand-messages)               |
| [Remote Control Data](https://doc-cdn.unitree.com/39/1642/en/39_1642_en)                              | Index only                     | [Interpretation and boundary](unitree-g1-plus.md#downloads-and-technical-documents)                                      |
| [Basic Services Interface](https://doc-cdn.unitree.com/39/1645/en/39_1645_en)                         | Read with model/version limits | [Interpretation and boundary](unitree-g1-plus.md#g1-hg-transport-configuration-and-separate-hand-messages)               |
| [High Motion Development](https://doc-cdn.unitree.com/39/1633/en/39_1633_en)                          | Index only                     | [Interpretation and boundary](unitree-g1-plus.md#downloads-and-technical-documents)                                      |
| [Sport Services Interface](https://doc-cdn.unitree.com/39/1646/en/39_1646_en)                         | Read with model/version limits | [Interpretation and boundary](unitree-g1-plus.md#locomotion-controller-switching-and-topic-specific-blending)            |
| [Motion Switcher Service Interface](https://doc-cdn.unitree.com/39/1651/en/39_1651_en)                | Read with model/version limits | [Interpretation and boundary](unitree-g1-plus.md#locomotion-controller-switching-and-topic-specific-blending)            |
| [RPC Routine](https://doc-cdn.unitree.com/39/1653/en/39_1653_en)                                      | Read with model/version limits | [Interpretation and boundary](unitree-g1-plus.md#locomotion-controller-switching-and-topic-specific-blending)            |
| [Arm Control Routine](https://doc-cdn.unitree.com/39/1654/en/39_1654_en)                              | Read with model/version limits | [Interpretation and boundary](unitree-g1-plus.md#locomotion-controller-switching-and-topic-specific-blending)            |
| [Head Control Interface](https://doc-cdn.unitree.com/39/1660/en/39_1660_en)                           | Read with model/version limits | [Interpretation and boundary](unitree-g1-plus.md#head-api-exact-portal-contract-absent-from-the-pinned-wrapper)          |
| [Arm Action Inferface](https://doc-cdn.unitree.com/39/1655/en/39_1655_en)                             | Read with model/version limits | [Interpretation and boundary](unitree-g1-plus.md#preset-arm-actions-and-the-internally-wired-hand-sdk-route)             |
| [Internal wiring dexterity hand control interface](https://doc-cdn.unitree.com/39/1656/en/39_1656_en) | Read with model/version limits | [Interpretation and boundary](unitree-g1-plus.md#preset-arm-actions-and-the-internally-wired-hand-sdk-route)             |
| [More Cases](https://doc-cdn.unitree.com/39/1634/en/39_1634_en)                                       | Read with model/version limits | [Interpretation and boundary](unitree-g1-plus.md#operating-chapters-filed-under-g1-still-need-exact-model-qualification) |
| [RL Control Routine](https://doc-cdn.unitree.com/39/1657/en/39_1657_en)                               | Read with model/version limits | [Interpretation and boundary](unitree-g1-plus.md#local-audio-service-and-historical-training-resources)                  |
| [Ros2 Communication Routine](https://doc-cdn.unitree.com/39/1658/en/39_1658_en)                       | Read with model/version limits | [Interpretation and boundary](unitree-g1-plus.md#shared-ddsrpc-apis-and-installed-version-checks)                        |
| [DDS Communication Routine](https://doc-cdn.unitree.com/39/1659/en/39_1659_en)                        | Read with model/version limits | [Interpretation and boundary](unitree-g1-plus.md#shared-ddsrpc-apis-and-installed-version-checks)                        |
| [Debugging Specification](https://doc-cdn.unitree.com/39/1635/en/39_1635_en)                          | Read with model/version limits | [Interpretation and boundary](unitree-g1-plus.md#operating-chapters-filed-under-g1-still-need-exact-model-qualification) |

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

The current portal expansion reviews 37 supplied records for this collection, preserving exact-model/shared-service/other-model distinctions and source/API mismatches. Existing manual page indexes and source-specific safety/power statements remain in place. No vendor source, SDK, ROS, DDS, simulator, physical hardware, charging, motion, calibration or flashing was executed. Only original offline parsing/AST/synthetic checks are validation evidence.

Reviewed November 24, 2026: G1+ product text and its selected original figure; pinned `unitree_ros` README; the pinned C++/Python SDK2 file trees. The actual pinned G1+ URDF is now read as XML, and all 37 supplied G1+ developer records are reviewed with exact-model versus legacy G1 applicability made explicit. Linked videos, unselected figures, driver artifacts and hardware behavior remain separately bounded.

**Readiness:** source-bounded manufacturer-reference draft. Exact store/SKU, manuals/power/stop, active hardware mapping, SDK target, firmware pairing and first live state contract remain unresolved. The source-inspection procedure and generic synthetic log check are the first results supplied.

**Vendor software execution:** not run; no SDK install/build/import, ROS or DDS. **Hardware validation:** not run; no power, tactile interaction, motion, charging, calibration or flashing. The standalone seven-case synthetic example was executed successfully; no physical compatibility is established by that result.

**Related documentation:** [Unitree model and development directory](./).

**Related documentation:** [Unitree model and development directory](./).
