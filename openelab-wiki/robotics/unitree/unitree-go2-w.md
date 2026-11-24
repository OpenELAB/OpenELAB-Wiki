---
description: >-
  Match Go2-W U1–U5, understand wheeled startup and controller modes, inspect
  DDS wheel state, faults, video and LiDAR, and resolve pinned SDK/API
  differences.
---

# Unitree Go2-W U1–U5: wheeled hardware, startup and SDK status

{% hint style="info" %}
[**View Unitree Go2W U1 on OpenELAB**](https://openelab.io/products/unitree-go2w-u1-wheeled-robotic) — SKU `Unitree-Go2W-U1`\
[**View Unitree Go2W U2 on OpenELAB**](https://openelab.io/products/unitree-go2w-u2-wheeled-robotic) — SKU `Unitree-Go2W-U2`\
[**View Unitree Go2W U3 on OpenELAB**](https://openelab.io/products/unitree-go2w-u3-wheeled-robotic) — SKU `Unitree-Go2W-U3`\
[**View Unitree Go2W U4 on OpenELAB**](https://openelab.io/products/unitree-go2w-u4-wheeled-robotic) — SKU `Unitree-Go2W-U4`\
[**View Unitree Go2W U5 on OpenELAB**](https://openelab.io/products/unitree-go2w-u5-wheeled-robotic) — SKU `Unitree-Go2W-U5`

**Model:** Unitree Go2-W wheeled quadruped · **Options:** five distinct store packages, each with one catalog variant; package-specific engineering configurations require the delivered bill of materials. Prices, availability and shipping are on the store pages.
{% endhint %}

## Product overview <a href="#product-overview" id="product-overview"></a>

Unitree Go2-W combines twelve leg joints with four wheel drives and 7-inch pneumatic tires. This guide separates the current manufacturer platform specification from OpenELAB's U1–U5 package names, interprets the exact **Go2-W User Manual V1.1**, and provides an app-status first result plus a conditional read-only SDK checkpoint. The 16-page Go2-W manual is accessible and was reviewed with original-image checks of its interface and startup figures. Its hardware revision and several inconsistent specifications still require comparison with the delivered unit; the leg-only Go2 manuals are not substitutes. [Official platform](https://www.unitree.com/go2-w/), [Go2-W V1.1 manual](https://marketing.unitree.com/article/en/Go2-W/User_Manual.html)

![Unitree Go2-W wheel-legged platform with pneumatic tires](../../.gitbook/assets/unitree-batch1-6d0bce8691aa5e94.png)

_Original Unitree product image, linked from its Go2-W page. It illustrates the platform, not a connector pinout or the contents of every U1–U5 package; image rights remain with the source._

### What do U1, U2, U3, U4 and U5 mean? <a href="#what-do-u1-u2-u3-u4-and-u5-mean" id="what-do-u1-u2-u3-u4-and-u5-mean"></a>

| OpenELAB package | Verified listing identity | What can be concluded from the listing                                             | What remains unresolved                                                                         |
| ---------------- | ------------------------- | ---------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| U1               | `Unitree-Go2W-U1`         | Go2-W robot listing; optional Orin NX expansion mentioned                          | Exact compute, sensors, charger, controller revision and expansion contents                     |
| U2               | `Unitree-Go2W-U2`         | Separate Go2-W robot listing                                                       | No independently established U2-specific hardware difference from U1/U3                         |
| U3               | `Unitree-Go2W-U3`         | Separate Go2-W robot listing                                                       | No independently established U3-specific sensor or compute upgrade                              |
| U4               | `Unitree-Go2W-U4`         | Separate Go2-W robot listing                                                       | No independently established U4-specific navigation entitlement or compute upgrade              |
| U5               | `Unitree-Go2W-U5`         | Store describes a stabilized visible-light/thermal payload and excludes the D1 arm | Payload manufacturer/model, calibration, API, electrical interface, mounting and delivered mass |

These identities were matched to actual catalog product and variant records and observed OpenELAB search links on 24 November 2026. The current Unitree platform page has one Go2-W parameter table, not five U-number tables. A higher U number is therefore not proof of a particular GPU, sensor, autonomous behavior or SDK feature. U5's payload description is store evidence; it is not a reviewed manufacturer payload manual. See the five purchasing links above for exact listing scope.

For the leg-only Air/Pro/EDU comparison, use the separate **Unitree Go2 Air, Pro and EDU guide** in this series. Do not load a Go2 configuration merely because a library path contains `go2`.

## Applications <a href="#applications" id="applications"></a>

Go2-W is suitable for supervised mobile-robot research, teaching wheel-and-leg kinematics, and logging robot status on an appropriately commissioned platform. Optional compute can support perception development after its exact software image, power budget and mechanical mounting are verified. Unitree explicitly lists secondary development for Go2-W. [Platform capabilities](https://www.unitree.com/go2-w/)

Navigation, route following and payload transport are integration projects: a demonstration video does not establish localization accuracy, braking distance or unattended deployment suitability. Thermal work on U5 additionally needs the payload's own radiometric calibration and software documentation. Go2-W V1.1 p. 2 requires 5–35 °C, dry non-dusty conditions, traction, line-of-sight control and at least 2 m clearance. It explicitly says the robot is not waterproof or dustproof. Do not infer an ingress or functional-safety rating from the outdoor product image. No tire pressure or service torque was established. [Exact Go2-W safety page](https://marketing.unitree.com/article/en/Go2-W/User_Manual.html)

## Specifications <a href="#specifications" id="specifications"></a>

The values below are manufacturer-reported platform values, not measurements of an OpenELAB package. Dimensions retain the source's order because the page does not label axes. [Unitree Go2-W parameter table and footnotes](https://www.unitree.com/go2-w/)

| Parameter                  | Current Go2-W platform value                                                                         | Integration meaning                                                                                                              |
| -------------------------- | ---------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| Standing envelope          | 70 × 43 × 50 cm                                                                                      | Confirm mounting and clearance against the actual payload and robot                                                              |
| Mass with battery          | About 18 kg                                                                                          | Added compute/gimbal/arm mass is not included by inference                                                                       |
| Electrical voltage         | 33.6 V                                                                                               | A platform voltage entry, not a third-party supply specification or connector pinout                                             |
| Payload                    | Approximately 8 kg; maximum approximately 12 kg                                                      | No load position, duty cycle or dynamic derating curve supplied                                                                  |
| Speed                      | 0–2.5 m/s                                                                                            | Not a safe initial test speed or braking guarantee                                                                               |
| Maximum climb/drop height  | Less than 70 cm                                                                                      | A capability claim, not a first-use obstacle procedure                                                                           |
| Maximum climb angle        | 35°                                                                                                  | Terrain/load conditions unspecified                                                                                              |
| Main compute               | 8-core high-performance CPU                                                                          | CPU model, RAM, storage and image version not specified                                                                          |
| Actuation                  | 16 motors in the table                                                                               | SDK mapping resolves twelve leg joints plus four wheel drives                                                                    |
| Maximum joint torque       | About 45 N·m for the largest motor                                                                   | Unitree says actual maxima differ across the 16 motors; not a continuous rating for every joint                                  |
| Tires                      | 7-inch pneumatic                                                                                     | Pressure, replacement procedure and fastener torque not established                                                              |
| Perception                 | Super-wide-angle 3D LiDAR; HD wide-angle camera                                                      | V1.1 describes L2; delivered model, frame rate, calibration and point-cloud interface require confirmation                       |
| Connectivity               | Product page lists Wi-Fi 6, 4G, Bluetooth                                                            | 4G conflicts with V1.1 p. 3 capability cells; confirm exact firmware/region, provisioning and carrier support                    |
| Included platform features | Product page lists manual controller, app support, front light, voice, OTA and secondary development | Voice/avoidance/tracking capability conflicts are recorded below; exact firmware/region and accessory revision must be confirmed |
| Compute expansion          | Multiple options, including Orin NX                                                                  | Optional; no fixed TOPS or image inferred                                                                                        |
| Battery                    | Long-endurance, 15,000 mAh                                                                           | Exact part number, chemistry and management limits require the battery documentation                                             |
| Endurance                  | 1.5–3 h                                                                                              | Conditions and package payload change endurance                                                                                  |
| Charger                    | Fast charger, 33.6 V / 9 A                                                                           | Confirm actual battery/charger pairing before charging                                                                           |

### Store claims that require reconciliation <a href="#store-claims-that-require-reconciliation" id="store-claims-that-require-reconciliation"></a>

| Claim found in OpenELAB listings                                                               | Current official evidence                                                                                         | Engineering decision                                                                                                              |
| ---------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| U1 standing 70 × 31 × 40 cm; 2–4 h endurance                                                   | Go2-W table says 70 × 43 × 50 cm and 1.5–3 h                                                                      | Use current platform table for preliminary planning; obtain exact U1 revision confirmation before fit/runtime commitments         |
| U2–U4 45° slope, 23 cm stairs and 1.5 m standing jump                                          | Current page gives 35° and a separate less-than-70 cm climb/drop entry; no matching stair/jump specification read | Do not convert these into operating limits or attempt them                                                                        |
| U1 −20 to 55 °C, about 5 h charging, L1 identity/FOV                                           | Not established in the reviewed current Go2-W table                                                               | V1.1 p. 2 specifies 5–35 °C robot use; charging procedure remains unresolved for the exact pack. Do not import Go2 battery limits |
| U5 gimbal 0.01° accuracy; 640 × 512 thermal imager; 8–14 µm; gain-dependent temperature limits | Store lists these, but no exact OEM payload manual was read                                                       | Treat as procurement claims pending payload identity and calibration evidence                                                     |

### Manufacturer sources also disagree: retain the revision boundary <a href="#manufacturer-sources-also-disagree-retain-the-revision-boundary" id="manufacturer-sources-also-disagree-retain-the-revision-boundary"></a>

The Go2-W V1.1 manual describes **L2 at 360° × 96°**, and its revision-history entry says L1 was replaced by L2. Its printed date for V1.1 is **4 June 2016**, preceding its V1.0 entry of 18 December 2024; the original image confirms this inconsistency. The filename's 2026 directory is not authority to silently correct the printed date. Identify the manual by V1.1 and its preserved source, and verify the delivered LiDAR before selecting L1/L2 software. [V1.1 pp. 3, 16](https://marketing.unitree.com/article/en/Go2-W/User_Manual.html)

| Topic              | Source discrepancy                                                                                                                                                                                              | Consequence                                                                                                                                                                |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Speed              | Platform table 0–2.5 m/s; manual p. 3 says 2 m/s; manual p. 14 says 3.5 m/s and includes an Air exception                                                                                                       | No reconciled operating maximum for the purchased package; do not test a headline maximum                                                                                  |
| Slopes / steps     | Platform 35° / less than 70 cm climb/drop; manual p. 14 gives 40°, 16 cm advice and an 18 cm caution, including Air text                                                                                        | Different claims cannot form a safe stair/slope procedure; first check stays on level ground                                                                               |
| Endurance          | Platform 1.5–3 h; manual p. 14 says 1–2 h for alternating unloaded standing/walking                                                                                                                             | Record workload and actual battery; do not promise either figure                                                                                                           |
| Feature capability | V1.1 p. 3 has hollow Go2 W cells for intelligent avoidance, 4G image transmission, ISS and voice; p. 4 nevertheless describes built-in 4G/eSIM and p. 11 Chinese voice; current product page lists 4G and voice | Confirm the delivered firmware, region and enabled features before using 4G, voice, tracking or avoidance. Do not infer support or absence from a single inconsistent cell |
| Compute            | Product page allows multiple expansion choices; manual p. 4 calls Orin NX 16GB / 100 TOPS standard, while p. 5's 16GB-headed table says 8GB memory                                                              | Confirm module/carrier/RAM and image; do not promise 16GB, 100 TOPS or a particular JetPack for every U package                                                            |

These are source conflicts, not measured defects. The Air exceptions in the Go2-W cautions are retained as evidence of a scope problem rather than accepted as Go2-W limits.

### Portal hardware specification and accessory scope <a href="#portal-hardware-specification-and-accessory-scope" id="portal-hardware-specification-and-accessory-scope"></a>

The [Go2-W portal comparison](https://doc-cdn.unitree.com/15/272/en/15_272_en) describes 16 drives, approximately 18 kg including battery, a 70 × 43 × 50 cm standing envelope, 28–33.6 V robot supply and an approximately 3000 W maximum-power headline. Its load figures are about 8 kg, with an approximately 12 kg limit; they are not continuous dynamic payload ratings for every gait or package. The maximum 45 Nm joint figure belongs to the largest joint type, not all sixteen actuators. Optional accessories in the same article are a catalog of possibilities, not the supplied U1–U5 bill of materials.

The portal quotes 0–2.5 m/s, 35° slopes and a below-70-cm climbing figure. The operation article separately describes high-speed forward motion up to 3.0 m/s and recommends climbing obstacles no higher than 50 cm. These are different mode/revision statements, not a combined terrain capability. The operating-environment table says 5–35°C and good weather; it supplies no ingress qualification for the whole assembly. Continue to retain the product/manual conflicts above rather than replacing them with whichever number is largest. [Hardware comparison](https://doc-cdn.unitree.com/15/272/en/15_272_en), [Operation Guide](https://doc-cdn.unitree.com/15/301/en/15_301_en)

The portal identifies battery **BT2-06**, 15000 mAh/432 Wh, nominal 28.8 V, 33.6 V charge limit, approximately 2.5 kg, a 9 A fast charger and claimed 1.5–3 h operation. Its charge-time cell is written `1h"15`; it is not a new independently measured charge time. This is evidence of the named portal configuration, not proof that every retailer package contains that exact pack or that another Go2 battery is interchangeable. The battery/charger nameplate and approved pairing still govern charging.

Head LiDAR is described as L2, 905 nm, 360° × 90°, 75 × 75 × 65 mm and a 12 V component supply. Optional navigation sensors are MID-360 (9–27 V component input, 360° horizontal/−7° to +52° vertical) or XT16 (9–36 V component input, ±15° vertical). A D435i accessory table gives 1280 × 720 at 30 fps or 848 × 480 at 90 fps depth modes and 0.105 m minimum depth distance. Those component tables do not authorize connection directly to the robot’s battery-voltage output or establish a delivered sensor/calibration. [About Go2-W](https://doc-cdn.unitree.com/15/272/en/15_272_en)

The camera description distinguishes 720p/180p streams at 25 fps from advertised capture/transmission capabilities up to 1080p30 or 720p60. Do not promise a measured 60-fps developer stream from those marketing conditions. The capability table marks intelligent companion, avoidance, front lighting and offline voice differently from descriptive text and indicator examples; Go App online interaction is not offline voice. Confirm actual enabled services and region.

The accessory tables describe a D1 six-axis servo arm (about 2.37 kg, ideal 500 g payload, 550 mm reach without gripper/670 mm with gripper, 24 V/2.5 A with 5 A maximum, DC5.5-2.1 power and Ethernet control). This is **D1**, not proof of D1-T teleoperation-kit inclusion or compatibility. The screen remote is described as a 5.5-inch 1080p Android 9 device with 2 GB RAM/16 GB storage, 10200 mAh 7.4 V battery and 20 W PD charging. The optional dual-camera and 3-in-1 lighting/megaphone attachments have separate power and interface requirements; the latter’s 16–60 V and sound/light figures are payload specifications, not robot input ratings or a guarantee of the U5 thermal payload’s identity. [Accessory specifications](https://doc-cdn.unitree.com/15/272/en/15_272_en)

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

### Identify, inspect and place the robot <a href="#identify-inspect-and-place-the-robot" id="identify-inspect-and-place-the-robot"></a>

Record the robot label and serial, U-package contents, battery/charger labels, remote model, installed LiDAR, expansion dock and payload. Confirm that the delivered platform is Go2-W. Inspect tires, feet, wheel assemblies and cables for damage or interference while powered off. The manual prohibits lifting the powered robot and side rolling with back-mounted accessories. Keep hands clear of joint pinch points. [Go2-W V1.1 pp. 2, 7, 14](https://marketing.unitree.com/article/en/Go2-W/User_Manual.html)

V1.1 p. 7 shows the pack entering from the side with its power switch upward; align it without forcing and confirm the latch click. Page 8 shows the **wheeled** startup posture: abdominal support flat, body horizontal, lower legs retracted and wheel feet placed on the level surface without the body trapping the legs. Use that exact drawing; the leg-only Go2 illustration is not the reference. Startup can raise the body automatically, so keep the wheel/joint motion envelope clear. Confirm the operator's stop method for the delivered controller/app before powering. [Original Go2-W startup figure, p. 8](https://doc-cdn.unitree.com/static/2026/6/4/0e82698010004c808b3d16654431bb64_2481x3509.png)

### Rear-panel connections and expansion dock <a href="#rear-panel-connections-and-expansion-dock" id="rear-panel-connections-and-expansion-dock"></a>

The following comes from original-image review of **Go2-W V1.1 pp. 4–6**. It is not transferred from consumer Go2. Compare the delivered panel and dock to those drawings before connection. [Exact manual](https://marketing.unitree.com/article/en/Go2-W/User_Manual.html)

| Robot rear-panel interface | Verified role and boundary                                                                                                                                                                                                    |
| -------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Power output               | 28.8 V DC output to the Orin NX 8/16GB dock's BAT input; not a robot supply input. Current limit, polarity drawing and mating harness specification remain unverified                                                         |
| RJ45 Ethernet              | Connection to user PC or Orin NX dock. No PoE or default address/credential implied                                                                                                                                           |
| SBUS                       | As viewed in the original p. 5 panel figure, left-to-right `NC/GND/SBUS`; explicitly **no power output**. Signal voltage, inversion, timing and channel mapping not supplied; no custom receiver wiring procedure established |

The dock figure identifies the following numbered ports. Its **16–60 V BAT input** rating belongs to the expansion dock, not to the Go2-W robot. Do not connect that range to the robot itself or connect both BAT inputs without the approved harness arrangement. [Original dock figure, p. 6](https://doc-cdn.unitree.com/static/2026/6/4/fa574f08f2874cc0a5468f2571f8a8c4_2482x3509.png)

| Dock figure label | Source-described function                     | Integration boundary                                                             |
| ----------------- | --------------------------------------------- | -------------------------------------------------------------------------------- |
| `[1]`             | `GH1.25-4PIN` 100M Ethernet / small servo arm | Four-pin signal mapping not supplied                                             |
| `[2]`             | M8 aviation connector / radar                 | No pin assignments or electrical levels established                              |
| `[3]`, `[4]`      | 16–60 V BAT inputs / Go2-W or small servo arm | Input polarity and shared-power arrangement require approved cable documentation |
| `[5]`             | RJ45 Gigabit Ethernet / robot                 | Distinguish from the user-side port                                              |
| `[6]`             | USB 3.2 Type-C / depth camera                 | Camera model, driver and calibration remain configuration-specific               |
| `[7]`             | Printed `RORCE-RECOVERY` service label        | Identifier preserved as printed; no recovery/flash sequence established          |
| `[8]`             | Type-A 5 V / 1 A user port                    | Port rating, not a total dock budget                                             |
| `[9]`             | 12 V / 3 A user output                        | Do not infer mating polarity from appearance                                     |
| `[10]`            | 5 V / 3 A user output                         | Combined power/fuse limits not supplied                                          |
| `[11]`            | RJ45 Gigabit Ethernet / user expansion        | Requires exact network provisioning                                              |
| `[12]`            | Full-featured Type-C / display                | Do not infer supported display modes or power delivery                           |

V1.1 p. 5's compute table lists Ampere GPU/Arm CPU, accelerators, external NVMe and H.265 encode/decode capabilities with a 10–25 W power-consumption entry. Its 16GB heading versus 8GB memory conflict prevents using it as a delivered module specification. Those entries are module-level claims, not guaranteed application throughput or a whole-carrier power budget. Obtain the exact module/carrier label, BSP/JetPack image, thermal configuration and storage BOM first.

### Battery, charging and maintenance boundaries <a href="#battery-charging-and-maintenance-boundaries" id="battery-charging-and-maintenance-boundaries"></a>

The platform page specifies a 15,000 mAh pack and 33.6 V / 9 A charger; the exact Go2-W manual confirms installation and startup/shutdown posture, but does not provide a separate charging/storage/protection table. Match the supplied pack and charger labels to an explicitly applicable battery manual before charging. Do not apply BT2-05/BT2-06 limits, LED codes, cutoff thresholds, storage temperatures or forced-off sequences from the leg-only Go2 battery manual without explicit Go2-W applicability.

V1.1 p. 12 requires low-down/prone/damping before power-off and removal of the pack for long storage. The page's normal sequence is short power press then a hold of 2 s; the figure caption reverses the press wording, so use the prose and confirm the supplied pack instruction before operation. Battery charging, custom power cables, tire service and unspecified fastener work remain outside this first result. No tire pressure, wheel service torque or total expansion-current budget was verified.

### Portal electrical and coordinate details <a href="#portal-electrical-and-coordinate-details" id="portal-electrical-and-coordinate-details"></a>

The [rear-interface article](https://doc-cdn.unitree.com/15/272/en/15_272_en) identifies the 28.8 V connector as an **output** supplying an expansion module’s BAT input. The RJ45 is the developer/network connection. Its SBUS definition is **NC / GND / SBUS from left to right in the illustrated view**, with no power output. SBUS voltage level and the mating harness are not established by that order; connector orientation must be checked against the actual drawing and hardware before wiring. The article includes a back mounting-hole drawing in millimetres, which is a mechanical reference rather than an invented bolt-torque or payload permission.

The [Payload article](https://doc-cdn.unitree.com/15/1285/en/15_1285_en) gives these dock roles. They describe the expansion dock, not the robot’s battery charger or bare pack:

| Dock connection     | Article contract and boundary                                                                                                                                       |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| XT30U-F inputs      | Two 16–45 V inputs, peak 60 V: dock supply and external arm supply. Peak is not continuous operating permission.                                                    |
| Low-voltage outputs | One 12 V/3 A and one 5 V/3 A external output; individual ratings do not establish a summed power budget.                                                            |
| Two RJ45 ports      | One robot-side Gigabit link and one user-side Gigabit link.                                                                                                         |
| M8 Ethernet/power   | Dedicated radar connection, including 12 V/2 A output; obtain the exact mating pinout.                                                                              |
| USB Type-A          | USB host only, USB3.2 Gen2, advertised 10 Gbps and 5 V/1 A.                                                                                                         |
| DP-capable Type-C   | USB2.0 host or DP1.4 alternate mode; 5 V/3 A output.                                                                                                                |
| Other Type-C        | USB3.2 Gen2, 5 V/2 A output. A connector shape does not establish its host/device role.                                                                             |
| GH1.25 four-pin     | Payload article calls it Gigabit Ethernet; the About table calls the corresponding dock connection 100 Mbit/s. Revision/rate is unresolved; do not invent a pinout. |

The About table also gives a broad 16–60 V dock range, unlike Payload’s 16–45 V continuous range. Treat this as a source/revision conflict before choosing a supply. Neither figure changes the robot supply or makes every accessory safe on its raw output. The full connector figure is [available from Unitree](https://doc-cdn.unitree.com/static/2024/5/14/7ca51de5cdc34b63bd6ff3a7ec74216b_1814x396.png); numeric roles above come from the read table, not an inferred pin assignment.

The four leg groups are FR, FL, RR and RL, each hip/thigh/calf. The portal describes hip rotation about body x and thigh/calf rotation about y, using the right-hand rule. Its nominal zero-pose figure is a coordinate illustration: calf zero lies outside the stated physical calf range. Source leg limits are hip ±48°, front thigh −200° to +90°, rear thigh −260° to +30°, and calf −156° to −48°. These are not wheel limits or automatically safe software target ranges. Wheel position/sign/radius and the delivered calibration need separate model-specific confirmation. [Joint coordinates and limits](https://doc-cdn.unitree.com/15/272/en/15_272_en)

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### Exact SDK scope and wheel differences <a href="#exact-sdk-scope-and-wheel-differences" id="exact-sdk-scope-and-wheel-differences"></a>

The reviewed Python repository contains explicit `example/go2w/` high- and low-level examples. This is actual Go2-W source evidence, stronger than inferring compatibility from a repository title. The snapshot is `814556d15970dd2ecf1c9984e845ca02ab07e206`, reviewed 24 November 2026. Its README and setup metadata list Python ≥3.8, `cyclonedds == 0.10.2`, NumPy and OpenCV; the package version is 1.0.1 with a BSD-3-Clause root license; it does not provide an exact Go2-W firmware compatibility range. [Pinned SDK README](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/README.md)

| Resource                     | Verified scope                                                                         | Limit                                                                                                                                                                                  |
| ---------------------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Python Go2-W examples        | Explicit wheel-platform high- and low-level files                                      | Examples contain active controls; do not execute them for first communication                                                                                                          |
| `unitree_go.msg.dds_`        | Go2-W example imports `LowState_`, `LowCmd_` and `SportModeState_` from this namespace | Shared message namespace does not make Go2 and Go2-W motor indexing equivalent                                                                                                         |
| `unitree_sdk2` C++           | README prebuild reference: Ubuntu 20.04 LTS, aarch64/x86\_64, GCC 9.4.0                | Architecture-specific prebuilt core libraries; building wrappers/examples does not establish a fully source-rebuildable control core or purchased-firmware support; no build performed |
| Developer quick-start portal | All 21 actual Go2-W CDN article bodies read                                            | Documented external-PC Ethernet network below; installed service/firmware pair still requires confirmation                                                                             |
| Firmware/OTA                 | Platform page lists OTA                                                                | No reviewed Go2-W recovery image, rollback package or flashing procedure                                                                                                               |

The exact wheel identifiers at the pinned Python source are `FR_w = 12`, `FL_w = 13`, `RR_w = 14`, `RL_w = 15`; leg motor indices are front-right 0–2, front-left 3–5, rear-right 6–8 and rear-left 9–11. These are SDK array indices, not connector pins or independent bus addresses. The leg-only Go2 map stops at 11. [Go2-W constants](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/example/go2w/low_level/unitree_legged_const.py)

The Go2-W high-level file imports `SportClient` from the `go2` package; this is an observed implementation reuse, not a reason to copy all Go2 motion functions. Its menu includes a `get_state` entry but the reviewed dispatch does not implement a corresponding `id == 7` branch. Its other branches can issue motion or recovery commands. Use a subscriber-only status check instead. [Reviewed Go2-W high-level source](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/example/go2w/high_level/go2w_sport_client.py)

Repository code availability does not establish the license of proprietary robot firmware, payload software or a commercial deployment. Retain the repository's license with redistributed code and review the delivered vendor terms. An accessible repository is not proof that firmware recovery or calibration tools are public.

### Portal service architecture and source versions <a href="#portal-service-architecture-and-source-versions" id="portal-service-architecture-and-source-versions"></a>

Go2-W uses continuous DDS topics for state/commands and DDS-based request/response clients for lower-rate queries and function changes. GStreamer/UDP video is a separate transport. The [SDK Concepts](https://doc-cdn.unitree.com/15/274/en/15_274_en) record delegates architecture to Go2; the [service overview](https://doc-cdn.unitree.com/15/277/en/15_277_en) explicitly delegates volume/light, LiDAR and multimedia to Go2. That delegation does not extend every Go2 motion, UWB, arm or navigation feature to a delivered Go2-W. Its [Obtain SDK](https://doc-cdn.unitree.com/15/275/en/15_275_en) page links SDK2 and separate STEP/URDF archives; those archives are resources, not inspected mechanical or simulation validation.

The [DDS chapter](https://doc-cdn.unitree.com/15/280/en/15_280_en) describes a factory initialized before publishers/subscribers, channel names paired with exact message types, publisher `InitChannel`/`Write`/`CloseChannel`, and subscriber callback initialization/close. `CreateSendChannel` sends and `CreateRecvChannel` receives; a copied subscriber paragraph incorrectly names the send function. Queued callbacks can avoid blocking the middleware thread, but a queue can also accumulate old data. Bound work and retain local receipt time, message counter/tick, model provenance and source pin. `GetLastDataAvailableTime` reports receive availability, with −1 before channel initialization; it is not a sensor timestamp or a physical synchronization guarantee.

At the pinned SDK2 revision **b7fec6020eb93d4c059a6edf19905e12a75a8d3d**, [ChannelFactory](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/channel/channel_factory.hpp) has `Init(domainId, networkInterface)` with two arguments, plus configuration-file/JSON-map overloads. The portal’s third `enableSharedMemory` argument is not available in that signature at this pin. The source [subscriber](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/channel/channel_subscriber.hpp) uses `CreateRecvChannel`. The portal’s `GetServerApiVersion` reference-return signature also differs from the pinned [client header](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/client/client.hpp), which returns `std::string` by value. Keep working two-argument initialization; do not turn the copied portal prototypes into a compile recipe for this pin.

Client initialization registers APIs. For a seconds-valued timeout at the pin, select `SetTimeout(float)`, for example `client.SetTimeout(2.0f)`. The [actual base header](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/client/client_base.hpp) also declares `SetTimeout(int64_t)` for internal timing units; an integer literal must not be described as seconds. Its default constant is 1000000 beside a one-second comment. Lease-enabled clients can block in `WaitLeaseApplied`; a lease is software coordination, not independent physical isolation. Record both client and server API versions and actual return status. Closing a channel releases that host object, not robot motor power or a previously selected controller mode. [DDS and RPC contract](https://doc-cdn.unitree.com/15/280/en/15_280_en)

| Common RPC code | Documented meaning                                                                                         |
| --------------- | ---------------------------------------------------------------------------------------------------------- |
| 3001            | Unknown error.                                                                                             |
| 3102–3106       | Request send failure, unregistered API, timeout, request/response mismatch, invalid response respectively. |
| 3107            | Invalid client lease.                                                                                      |
| 3201            | Response-send failure on the server; the table says it is not returned to the client.                      |
| 3202–3205       | Server internal error, unimplemented API, bad parameters, rejected request respectively.                   |
| 3206 / 3207     | Invalid server lease / lease already exists.                                                               |

These codes are not motor fault masks. Any nonzero documented failure must be handled; positive return values are not automatically success. A timeout is not evidence that a state-changing request was never executed. [RPC errors](https://doc-cdn.unitree.com/15/280/en/15_280_en)

### Service status and control ownership <a href="#service-status-and-control-ownership" id="service-status-and-control-ownership"></a>

The [RobotStateClient chapter](https://doc-cdn.unitree.com/15/281/en/15_281_en) describes service switching and interval/duration-based status reporting in seconds. Error 5201 means a switch execution error; 5202 identifies a protected service. It lists wheeled motion, underlying, network-switch, OTA, LiDAR, video and WebRTC services, but several labels contain copied spaces/capitalization. Discover and record the actual delivered service list rather than typing those labels as operational commands.

The pinned [RobotStateClient](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/go2/robot_state/robot_state_client.hpp) declares `ServiceList(vector<ServiceState>&)` and **`ServiceSwitch(name, swit, status_out)`**, unlike the portal’s two-argument prototype. `swit` requests 1 on or 0 off; do not confuse those request values with the separately returned service-status encoding. The older low-level article treats a listed status 0 as active. Confirm both RPC success and the returned current state; a missing service or failed query cannot mean “safe to take ownership.” `SetReportFreq` changes reporting, not motor-loop rate. [Robot-state API](https://doc-cdn.unitree.com/15/281/en/15_281_en), [basic-control example](https://doc-cdn.unitree.com/15/289/en/15_289_en)

Only one motion controller may own low-level commands. The portal example disables `wheeled_sport` with RobotStateClient. The pinned [Go2-W stand example](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/go2w/go2w_stand_example.cpp) instead uses [MotionSwitcherClient](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/b2/motion_switcher/motion_switcher_client.hpp) to inspect and release the current mode. Its namespace/path is `b2` even in this actual Go2-W example; this is source evidence for the example, not B2 hardware identity. Do not combine fragments from those ownership generations into an unverified procedure. A failed `CheckMode` followed by an empty name is not proof of release; the sample’s handling is insufficient as a production ownership gate. A receive-only subscriber needs neither release nor service shutdown.

### Go2-W high-level motion reference <a href="#go2-w-high-level-motion-reference" id="go2-w-high-level-motion-reference"></a>

The [Sports Services article](https://doc-cdn.unitree.com/15/283/en/15_283_en) uses `unitree::robot::go2::SportClient` for Go2-W. Its stand-up/down example moves the robot; it is not a connection test. These are documented behaviors and prerequisites, not commands to run as part of this guide’s first result:

| Interface             | Behavior and important state boundary                                                                                                                         |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Damp()`              | Requests damping, described as highest-priority software stopping. Gravity, inertia, wheels and a broken link still need an engineered independent stop plan. |
| `BalanceStand()`      | Switches to balanced standing with terrain-relative posture/height regulation.                                                                                |
| `StopMove()`          | Stops current movement and resets most internal movement parameters; does not disconnect power.                                                               |
| `StandUp()`           | Standing joint lock; article gives 0.44 m default height and says it may not respond on a steep slope.                                                        |
| `StandDown()`         | Lies down, then standby; article requires standing lock or damping before response.                                                                           |
| `RecoveryStand()`     | Active recovery to balanced standing, even if not fallen; requires damping or lying state.                                                                    |
| `Move(vx,vy,vyaw)`    | Body-frame translational and yaw-rate request; limits depend on mode. The article’s blanket m/s heading must not turn yaw rate into linear velocity.          |
| `SpeedLevel(level)`   | −1 slow, 0 normal, 1 fast; article says this affects default mode only.                                                                                       |
| `SwitchGait(d)`       | Portal describes 0 default, 1 terrain/stairs, 2 climbing. **Not declared in the pinned SportClient header.**                                                  |
| `GetState(names,map)` | Portal describes `speedLevel` and `gait` strings. **Not declared in the pinned SportClient header.**                                                          |

Source velocity ranges are default forward ±1.5 m/s, fast forward ±2.5 m/s, lateral ±0.6, yaw ±1.0; terrain forward ±0.7, lateral ±0.5, yaw ±1.0; climbing forward ±0.5, lateral ±0.4, yaw ±0.6. These are source envelopes, not validated commands or maximum safe speeds for a load. The source’s state map uses gait 0/1/2 for default/terrain/climbing and 3 inversion, with −1/−2/−3 standing lock/lying/damping; it lists speed states 0/1 although the setter also accepts −1. Preserve that asymmetry and check delivered telemetry before decoding.

The actual pinned [SportClient declarations](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/go2/sport/sport_client.hpp) and [Go2-W menu example](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/go2w/go2w_sport_client.cpp) explain the version boundary: `switch_gait` and `get_state` remain menu entries but their calls are commented out. Seeing “success” there proves no RPC occurred. The portal example also has `gait` with a trailing space, tests only `res < 0` even though positive codes can be failures, and retains the last selected option after `list` or invalid input. Its initial option is stand-up. Thus even a menu/list interaction is not a read-only demonstration. Blocking terminal input also means a 20 ms sleep target does not establish a measured 50 Hz command loop. The source comment says a single Move request expires after roughly a second without renewal; delivered behavior must be verified separately and must not replace an explicit stop procedure. [High Motion Control](https://doc-cdn.unitree.com/15/288/en/15_288_en)

### Low-level state, command layout and source defects <a href="#low-level-state-command-layout-and-source-defects" id="low-level-state-command-layout-and-source-defects"></a>

For DDS, the host **subscribes** to `rt/lowstate` and **publishes** `rt/lowcmd`. The [Basic Services article](https://doc-cdn.unitree.com/15/282/en/15_282_en) reverses those roles in two prose sentences; its topic names and message intent establish the correct direction. These are `unitree_go::msg::dds_` message types, not standalone actuator RS485 packets. A common 20-slot array is capacity, not evidence of twenty physical actuators.

| Indices | Actual Go2-W mapping                                           |
| ------- | -------------------------------------------------------------- |
| 0–2     | Front-right hip, thigh, calf.                                  |
| 3–5     | Front-left hip, thigh, calf.                                   |
| 6–8     | Rear-right hip, thigh, calf.                                   |
| 9–11    | Rear-left hip, thigh, calf.                                    |
| 12–15   | Front-right, front-left, rear-right, rear-left wheels.         |
| 16–19   | Spare capacity; no additional actuator permission established. |

One command comment incorrectly assigns RL wheel to 16; the same article’s feedback map and pinned [Go2-W constants](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/example/go2w/low_level/unitree_legged_const.py) use **15**. This guide uses that explicit wheel map, not the typo or a leg-only map. Wheel direction, gear/radius conventions and installed calibration still need confirmation before physical interpretation.

`LowCmd` carries FE EF verification bytes, motor commands, a BMS command, GPIO control and a CRC. `MotorCmd` has mode, target position, velocity, torque, stiffness and damping; mode 1 is FOC and 0 standby in this article. BMS `off=0xA5` requests battery shutdown. The article assigns GPIO bit 0 to autocharging disable and bit 1 to motor-power disable (cleared enables, set disables). Its motor-power prose still says twelve motors in this sixteen-drive article; do not assume the wheel-power behavior from that copied sentence. These are state-changing controls, excluded from the subscriber checkpoint.

`LowState` groups the following engineering observations. Retain raw fields and actual types; reasonable-looking numbers do not prove valid/fresh data:

| Group                | Fields and interpretation                                                                                                                                                                                                                                                                       |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Motor                | Mode, `q`, `dq`, `ddq`, `tau_est`, temperature, lost-packet counter and reserve words. The article calls `q_raw/dq_raw/ddq_raw` unused; do not reinterpret them as a calibrated second encoder. Reserve\[0] is its fault mask and reserve\[1] communication frequency.                          |
| IMU                  | Quaternion **w,x,y,z**, roll/pitch/yaw, x/y/z angular velocity and acceleration, temperature. A copied “switch” label is pitch; repeated index 0 comments are not an axis mapping.                                                                                                              |
| Battery              | Version, status, SOC, signed current, cycle count, two battery NTCs, MCU/MOS NTCs and 15 cell-voltage slots. Array capacity does not establish fifteen installed series cells. The excerpt’s status declaration is malformed; use the pinned generated type rather than compiling that excerpt. |
| Battery state values | Source codes 0 safe, 1 wake-up, 6 precharge, 7 charging, 8 discharge, 9 self-discharge, 11 alarm, 12 waiting-reset alarm, 13 recovery. Positive battery current means charging and negative discharging in this source; do not transfer that sign convention to every power-current field.      |
| Body                 | Four foot-force channels in FR/FL/RR/RL order; `tick` is described as a 1 ms counter, not an absolute timestamp. Forty raw remote bytes, `power_v`, `power_a`, winder current and board/charging temperatures are separate measurements.                                                        |
| Fans                 | Three RPM channels and a fourth bitmask for left-rear/right-rear/front blocked rotation.                                                                                                                                                                                                        |

The old IDL snippets use octets for several temperatures while comments describe signed values. At the pinned C++ revision, [LowState](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/go2/LowState_.hpp), [MotorState](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/go2/MotorState_.hpp) and [BmsState](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/go2/BmsState_.hpp) actually declare these temperature/NTC fields as `uint8_t`; the ROS article lists several as `int8`. Preserve that schema conflict and raw bytes until the delivered firmware/message pair establishes the interpretation. Neither treating 255 as a plausible 255°C nor blindly reinterpreting every byte as signed is justified by the conflicting excerpts. Reserved/unused version or serial fields likewise must not be promised as authoritative hardware identification. [Basic Services](https://doc-cdn.unitree.com/15/282/en/15_282_en), [ROS2 state definitions](https://doc-cdn.unitree.com/15/285/en/15_285_en)

### What the wheel-control demonstration actually does <a href="#what-the-wheel-control-demonstration-actually-does" id="what-the-wheel-control-demonstration-actually-does"></a>

The [Basic motion control article](https://doc-cdn.unitree.com/15/289/en/15_289_en) is an active state machine, despite printing sensor data. It folds the legs, stands, rotates wheels forward/backward, then lies down. It does not merely swing a calf as some copied setup text says. Its recurrent writer target is 2 ms; waiting 500 writer calls is approximately one second of intended scheduling, **not a check that any fresh feedback arrived**. The article’s service-list function also leaves a status uninitialized if the named service is missing and ignores the query’s return. Neither pattern is a production commissioning gate.

The pinned [Go2-W source](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/go2w/go2w_stand_example.cpp) initializes twenty command slots, with stop sentinels and zero gains, and then controls twelve legs plus four wheels after mode release. Its four phases progress through fold/stand/roll/lie targets. Within rolling it sends +3 rad/s wheel velocity for the first 40%, −3 for the next 40%, then zero; leg gains remain active. These are descriptions of hazardous demo behavior, not wheel speed settings to copy. The terminal’s “example done” flag does not terminate its infinite loop or stop repeated commands; it cannot be treated as motor isolation.

The source calculates a wordwise CRC32 over the SDK command representation excluding the final CRC word, seed FFFFFFFF/polynomial 04C11DB7. That is not permission to checksum arbitrary C++ object padding, DDS CDR network bytes, an HG humanoid message or an RS485 actuator packet the same way. Use the exact matched message implementation and reviewed serializer. No raw DDS encoder, stand demo or CRC-bearing motor command was executed here. A future controller must gate fresh valid state and confirmed exclusive ownership before publishing, handle every nonzero return, and have an independently engineered stop/recovery plan.

### ROS2 and Python integration reference <a href="#ros2-and-python-integration-reference" id="ros2-and-python-integration-reference"></a>

The [ROS2 chapter](https://doc-cdn.unitree.com/15/285/en/15_285_en) explains direct DDS/message compatibility rather than a required additional motor-control bridge. Its tested combinations are Ubuntu 20.04/Foxy and 22.04/Humble, with examples developed for Foxy and distribution-specific API adjustments required elsewhere. The source names CycloneDDS **0.10.2**, `rmw_cyclonedds_cpp`, generated DDS IDL dependencies and the `unitree_go`/`unitree_api` packages. A moving release branch in an install command is not an immutable compatibility pin.

Its setup sequence separates middleware compilation in a terminal without a sourced ROS environment from the subsequent ROS-dependent message-package build. The completed environment sources ROS and the local workspace, selects `RMW_IMPLEMENTATION=rmw_cyclonedds_cpp`, and supplies `CYCLONEDDS_URI` with the actual connected interface. Keep those environment changes in an isolated reviewed session rather than blindly changing every shell startup. Loopback configuration is for local communication/simulation; it is not proof that robot DDS is reachable. None of the source’s install, build, environment or ROS commands was executed here.

| ROS-facing path                         | Intended use and qualification                                                                                                                                                                                                                                        |
| --------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `/sportmodestate`, `/lf/sportmodestate` | Receive motion state: stamp/error, IMU, mode/gait/progress, body height, position/velocity/yaw speed, obstacle ranges, foot forces and body-frame foot positions/speeds. The article’s copied Go2 motion/gait enum is not a verified complete wheel-mode enumeration. |
| `/lowstate`, `/lf/lowstate`             | Receive low-level state described above; 20 slots retain 16 model-specific active indices.                                                                                                                                                                            |
| `/wirelesscontroller`                   | Receive normalized `lx/ly/rx/ry` and 16-bit keys; not the same format as the raw forty-byte remote block.                                                                                                                                                             |
| `/api/sport/request`                    | Publish state-changing `unitree_api::msg::Request` motion requests. Constructing a request object does not execute it until published, but publishing does.                                                                                                           |
| `/lowcmd`                               | Publish low-level joint/BMS/GPIO control. The source’s sentence saying “subscribing” while sending is a direction error.                                                                                                                                              |
| `/utlidar/cloud`                        | Point cloud visualization example uses `utlidar_lidar` as fixed frame. Confirm actual topic/frame and transforms for the delivered LiDAR; a rendered cloud is not obstacle-avoidance validation.                                                                      |

ROS-facing names do not automatically match the SDK’s `rt/` topic spelling; retain the mapping supplied by the matching environment. Listing topics and bounded state echo are diagnostic observations, unlike the example executables that publish walking or joint targets. A successful discovery step does not establish signed-temperature semantics, correct wheel signs, synchronization or actual control permission.

The [Python chapter](https://doc-cdn.unitree.com/15/286/en/15_286_en) requires Python ≥3.8, CycloneDDS 0.10.2, NumPy and OpenCV. If the middleware cannot be located, its remedy is a reviewed local CycloneDDS install plus a correctly selected `CYCLONEDDS_HOME`/build-prefix path before installing the wrapper. Match interpreter ABI and library release; do not replace dependencies indiscriminately to suppress an import error. Its camera example needs a graphical environment and exits on ESC. Camera readout and wireless-state display do not require motion-service shutdown. The pinned Python revision and the conditional subscriber above remain the concrete source reference; no vendor package was imported, installed, built or run for this guide.

### Delegated Go2 volume, image and LiDAR services <a href="#delegated-go2-volume-image-and-lidar-services" id="delegated-go2-volume-image-and-lidar-services"></a>

The Go2-W service overview explicitly refers to Go2’s VUI, LiDAR and multimedia chapters. The following contracts were actually read, in addition to the 21 Go2-W records. They remain conditional on the delivered sensor, running service and matching firmware; cross-reference is not proof that a headlight or avoidance function is present in every package. [Go2-W delegation](https://doc-cdn.unitree.com/15/277/en/15_277_en)

**VUI:** [Volume and Lighting](https://doc-cdn.unitree.com/6/75/en/6_75_en) documents `SetBrightness`/`GetBrightness` and `SetVolume`/`GetVolume`, values 0–10 and error 100 for invalid parameters. Getters are requests; setters change output. Pinned [VuiClient](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/go2/vui/vui_client.hpp) also declares switch get/set methods. A declared method does not resolve the Go2-W lighting-capability conflict or establish an exact firmware pair. Check return zero before using an output parameter; do not run a cycling example as a passive query.

**Camera:** [Multimedia Services](https://doc-cdn.unitree.com/6/53/en/6_53_en) separates an RPC JPEG sample from a continuous H264 stream. `VideoClient::GetImageSample(vector<uint8_t>&)` returns encoded image bytes, not a decoded pixel array; the pinned [VideoClient](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/go2/video/video_client.hpp) declares that method. The source’s JPEG loop saves files every three seconds. Bound capture/storage, inspect the returned status and decode result, and avoid writing stale previous bytes after a failed request.

The documented receive path is multicast **230.1.1.1, UDP 1720**, RTP/H264 depayload → H264 parse/decode → color conversion → display or OpenCV appsink. Use the actual robot-connected multicast interface. Although the introduction says “directed UDP,” that address and pipeline describe multicast. The article reports **1280 × 720 at 15 Hz**, with 100° horizontal/56° vertical view, unlike the About page’s broader camera-capability claims. Treat these as source-specific modes, not a verified 60-fps development stream.

A GStreamer-enabled OpenCV backend is necessary for the shown `CAP_GSTREAMER` pipeline. The source illustrates an OpenCV 4.1.1 build and GStreamer base/good/bad/ugly/libav and display plugins; these are historical build choices, not a mandate to install that old revision or every plugin on a delivered system. Confirm GStreamer in the existing OpenCV build information and test the negotiated format in a later reviewed environment. The sample can drop buffered frames with appsink settings; the application must still bound queue age, check `read()` success, reject empty frames and close resources on exit. The chapter does not establish a sensor-clock timestamp for each decoded frame. No streaming program, package installation or camera request was executed here.

**LiDAR:** [LiDAR Services](https://doc-cdn.unitree.com/6/51/en/6_51_en) documents the following DDS contracts; the `rt/` prefix is removed in its ROS-facing examples:

| Topic                         | Type / interpretation                                                                                                                                               |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `rt/utlidar/cloud`            | `sensor_msgs::msg::dds_::PointCloud2_`, raw cloud in `utlidar_lidar`.                                                                                               |
| `rt/utlidar/cloud_deskewed`   | Deskewed cloud in `odom`. The article has spelling/spacing typos elsewhere; this spelling appears in its visualization section. Confirm the actual published topic. |
| `rt/utlidar/height_map_array` | `unitree_go::msg::dds_::HeightMap_`: timestamp/frame, resolution, width/height, xy origin and float heights.                                                        |
| `rt/utlidar/range_info`       | `geometry_msgs::msg::dds_::PointStamped_`; x/y/z mean **front/left/right ranges**, not a Cartesian point position.                                                  |
| `rt/utlidar/switch`           | Publish `std_msgs::msg::dds_::String_` with `ON` or `OFF`; changes LiDAR operation and rotation. Not a receive-only diagnostic.                                     |

Parse PointCloud2 using its field descriptors/offsets/types, endianness, `point_step`, `row_step`, dimensions and data size; do not assume packed xyz floats. Unordered clouds normally use height 1, but width alone is not a universal point count. Check frame/timestamp and the dense/invalid-point indication before transforming. Deskew uses motion-state/IMU/odometry and the article says its reference time is the last point in a frame; the misspelled `rt/portmodestate` sentence is not a topic name to copy. `odom` is not a geodetic or drift-free global reference.

For a height map, cell `(ix,iy)` uses `data[ix + width*iy]` at xy `(origin_x + ix*resolution, origin_y + iy*resolution)`. The example reserves **1.0e9** for an empty cell; do not treat that as a real obstacle height. Validate dimensions, exact data length, finite positive resolution and finite coordinates, and skip invalid/empty cells. The map depends on the manufacturer motion program’s odometry; disabling that program for a custom controller can stop height-map publication. This is a dependency, not a reason to leave competing command owners active. Old height-map example code uses `DdsEasyModel`; it is not presented here as a current pinned ChannelSubscriber compile recipe.

For visualization, raw cloud needs the LiDAR frame; the deskewed cloud/map use `odom`. Increasing RViz decay time accumulates old points for display and does not improve sensor freshness or prove avoidance. An obstacle-distance message has three directional values and cannot represent every overhang, drop-off or moving object. Perception availability and motion-avoidance permission remain distinct.

### Additional dock-package references and recovery boundary <a href="#additional-dock-package-references-and-recovery-boundary" id="additional-dock-package-references-and-recovery-boundary"></a>

The separately read [Go2 Expansion Dock Configuration chapter](https://doc-cdn.unitree.com/6/110/en/6_110_en) explicitly lists **Go2-W SLAM service ZIPs**, making these relevant named resources alongside the Go2-W portal’s Payload cross-reference. Its 2 September 2025 entries describe relocalization fixes and YSN verification; its 1 April 2026 entries describe MID360s adaptation, with separate Go2 and Go2-W targets. They are listed packages, not evidence that a delivered U-package, carrier image, LiDAR or firmware is compatible. The June 2025 odometer package is another distinct entry. Obtain a confirmed complete revision pairing before any update.

The chapter describes a dock at **192.168.123.18**, distinct from the robot `.161` and an external host. Its display example uses the DP-capable Type-C port with a Type-C/HDMI adapter and requires adequate cooling. A Nano 8 GB/40-TOPS versus NX 16 GB/100-TOPS comparison contains an NX memory row saying 8 GB; that contradiction must not choose the installed module. Factory login details in the original chapter were not used or verified for any device.

Its module web interface is described as selecting/uploading a manufacturer package, starting an update, deleting an uploaded package or rolling back the previous module-service version. It explicitly says factory restore is not supported by that interface. That **module rollback** is not robot motion-firmware rollback, a battery update or a guarantee of recovery after loss of power.

Two other repair descriptions are board/image-specific service work. Type-C power loss after deletion of `rc.local` is diagnosed with the `PP.06` GPIO enable state; the described repair restores a boot service and changes GPIO/register setup. A reading of 1 sends the investigation toward hardware in that chapter. The Type-A/USB2 problem has a separate device-tree update archive, contrasting a March 2023 tree with a September 2025 target. Those procedures change persistent boot/hardware configuration; they are not generic USB driver fixes or a reason to run an uninspected script on Go2-W. No archive or repair was executed.

The same chapter describes physical NVMe removal, host block-device identification, a compressed whole-system image backup and a reverse image write for recovery. Formatting or writing the wrong target destroys data; an exact carrier/module image and a separately reviewed service plan are prerequisites. The source mentions at least 300 GB free space and multi-hour transfer times, not a guaranteed duration or an image-integrity check. Its latest Go2 NX image name is `go2_nx_Jetpack5.1.1_20250930.img.bz2`; a Nano filename appears without a latest download URL, while historical NX/Nano links are separate. This is actual read **Go2 dock documentation**, not independent confirmation that every Go2-W dock can use those images. Robot firmware recovery, complete Go2-W carrier compatibility and calibration remain unresolved.

Named Go2-W resources, **listed only**: [September 2025 SLAM package](https://oss-global-cdn.unitree.com/static/ed80622f2fad4cfdb2e91558eb77eb18.zip), [April 2026 MID360s SLAM package](https://oss-global-cdn.unitree.com/static/733c1dd4422147f184be6cda92db5b4f.zip). The read chapter, not a filename alone, establishes their labels. All update/recovery work is outside this guide’s offline and receive-only checkpoints.

### Go2-W package-scoped SLAM and navigation reference <a href="#go2-w-package-scoped-slam-and-navigation-reference" id="go2-w-package-scoped-slam-and-navigation-reference"></a>

The separately read [SLAM/Navigation article](https://doc-cdn.unitree.com/6/111/en/6_111_en) explicitly configures **Go2/Go2\_W** variants, gives a Go2-W navigation speed range and is accompanied by named Go2-W packages in the [dock resource chapter](https://doc-cdn.unitree.com/6/110/en/6_110_en). This establishes a versioned manufacturer reference, not every U1–U5 delivery's navigation entitlement or commissioning. Confirm the exact Go2-W dock, matched officially purchased MID-360/XT16, service package and firmware before applying the reference. The article requires robot software ≥1.1.7 for its latest service, prohibits radar hot-plugging, and limits intended operation to static, feature-rich, flat indoor areas smaller than 25 × 25 m. These conditions do not qualify unattended industrial navigation.

The robot supplies motion information; the dock runs mapping/localization/navigation. Network roles in that chapter are robot **192.168.123.161**, dock **192.168.123.18**, LiDAR **192.168.123.20**, and a separate nonconflicting host. DDS interface settings in the dock’s `cyclonedds.xml` must match its actual dock-network interface. The article warns its supplied SLAM/driver/keyDemo binaries conflict with initialized ROS/ROS2 environments, even though another diagnostic step uses ROS2 topic listing. Keep those tool environments separate; do not merge them into an untested launch recipe.

Use the actual **Go2\_W `T_Dog2lidar`** entry and delivered radar/mount, not the Go2 numeric extrinsics from the shared article. `lidar_type` and `lidar_ysn` must match the actual radar and robot; obtain unknown YSN from Unitree. The mere presence of a separate model configuration is not a measured transform or proof of calibration.

Mapping requires valid odometry/IMU and point clouds before motion. The application describes saving a PCD map, then loading it for localization and supplying an initial pose near the mapping origin. An empty initial visualization can simply mean no valid initial pose was supplied. Localization output/TF and the chosen map must agree before any navigation request. A direct-pose navigation request does not establish a certified collision-free route.

### SLAM requests, topics and completion evidence <a href="#slam-requests-topics-and-completion-evidence" id="slam-requests-topics-and-completion-evidence"></a>

The documented service is **`slam_operate`**, version **`1.0.0.1`**. Requests use a JSON `data` object; common replies contain `succeed`, `errorCode`, `info` and `data`. Check both RPC outcome and application fields. A request reply is not navigation arrival. Source JSON snippets contain comments/missing commas, so they are explanatory sketches rather than ready-to-send JSON. [Service contract](https://doc-cdn.unitree.com/6/111/en/6_111_en)

| API ID      | Function and input content                                                                                                                      |
| ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 1801        | Start mapping with fixed `slam_type: "indoor"`.                                                                                                 |
| 1802        | End mapping and save to the selected `address` PCD path on the dock. Review paths and existing files first.                                     |
| 1804        | Initialize localization with xyz, quaternion q\_x/q\_y/q\_z/q\_w and the PCD address. Navigation JSON uses **xyzw**, unlike low-state IMU wxyz. |
| 1102        | Navigate to targetPose, obstacle `mode` and speed. Mode 1 stops for obstacles; 0 requests bypass. This autonomously moves the robot.            |
| 1201 / 1202 | Pause / resume navigation; not power isolation.                                                                                                 |
| 1901        | Close SLAM; a service lifecycle change, not an independent motor stop.                                                                          |

The direct navigation target must be within **10 m** of the current position, with straight-line motion described by the source. The chapter gives **Go2-W 0.2–1.5 m/s**, distinct from Go2 0.2–1.0 m/s; these are service envelopes, not safe operating speeds for a particular surface or load. For bypass it requires a navigable width at least 0.8 m and obstacle width no more than 0.5 m; field-of-view limits mean obstacles should be at least 20 cm high. Those restrictions leave important low-object/drop-off/visibility limits and do not guarantee avoidance.

| DDS topic                           | Type / use                                                       |
| ----------------------------------- | ---------------------------------------------------------------- |
| `rt/unitree/slam_mapping/points`    | PointCloud2 mapping cloud.                                       |
| `rt/unitree/slam_mapping/odom`      | Odometry mapping pose.                                           |
| `rt/unitree/slam_relocation/points` | PointCloud2 localization cloud.                                  |
| `rt/unitree/slam_relocation/odom`   | Odometry localization pose.                                      |
| `rt/slam_info`                      | String JSON: robot\_data, pos\_info/mapping\_info or ctrl\_info. |
| `rt/slam_key_info`                  | String JSON: task\_result completion feedback.                   |

`robot_data` includes motor temperatures/errors, battery current **mA**, voltage **mV**, percentage and temperature, CPU temperature/utilization/memory/frequency (MHz); motion/gait fields are marked temporarily unavailable. Position records include currentPose and map name/path; control records include target/start poses, state-machine pause/planning/direction flags, velocities, obstacle state/time and progress. `task_result` identifies the target and `is_arrived`. Preserve sec/nanosec and receipt age across these records. A true `succeed` at request time is not `is_arrived`, and missing feedback is not a successful task.

The supplied service/driver/keyDemo launch path is active. The tutorial requests MAXN power mode and large socket buffers, and includes broad permission changes; those are image-specific modifications, not required first-result actions. Review targeted permissions and actual resource limits rather than reproducing recursive world-write commands. It discourages competing heavy processes such as RViz on the dock, describes thermal throttling/localization failures and recommends no more than about 30 minutes continuous operation until the CPU cools. Disabling native avoidance for this controller is also an explicit ownership/protection change, not a harmless display setting. No launch, update, navigation or configuration edit occurred here.

### Recharge package label versus qualified Go2-W installation <a href="#recharge-package-label-versus-qualified-go2-w-installation" id="recharge-package-label-versus-qualified-go2-w-installation"></a>

The separately read [Aruco Recharge article](https://doc-cdn.unitree.com/6/298/en/6_298_en) opens with **Go2 with NX dock** as its applicability note, yet also lists a Go2-W archive. Preserve this difference: the named archive does not by itself qualify every Go2-W camera, pad, carrier image or delivered firmware. The following is the shared package's documented functional reference, conditional on a manufacturer-confirmed Go2-W installation; it is not an instruction to run the Go2 binary on Go2-W.

The front camera approaches a single stationary marker facing it within 1.5 m. The exact family token is `36h11`, with a 0.1075 m black square, about 1 cm white margin, matte rigid flat printing and specified x-left/y-down orientation. If actual black size differs, its `aruco_size` parameter must match. Do not substitute an arbitrary ArUco dictionary because of the chapter title, infer scale from a preview, or use the head indicator for required nighttime lighting. Clear conflicting markers from view.

The documented ROS String input `/aruco_cmd` value `aruco_start` **initiates autonomous movement**. Its `/aruco_state` `aruco_arrive` reports pad posture, not completed charging; `aruco_success` follows roughly ten seconds of detected charging, while `aruco_failed` follows up to three unsuccessful attempts. Failed attempts may stand and retry. Review/stop the node after failure instead of sending an unbounded request loop; the article establishes no cancellation API or independent stop system. Record the matched DDS representation only after confirming the delivered package.

CSV logging and binary/SDK-library troubleshooting are documented, with inconsistent aruco\_charge/aruco\_recharge program names. Match the supplied SDK/middleware ABI and actual library lookup path before any approved execution; global symlink replacement or static-library deletion is not a general repair. No archive was opened, calibration performed or recharge process run. These shared package details complement, and do not replace, the Go2-W manual's charging and physical power boundaries. [Shared source, including named Go2-W resource](https://doc-cdn.unitree.com/6/298/en/6_298_en)

## Getting started <a href="#getting-started" id="getting-started"></a>

### First working result: Go2-W app identity and normal startup <a href="#first-working-result-go2-w-app-identity-and-normal-startup" id="first-working-result-go2-w-app-identity-and-normal-startup"></a>

Prerequisites are an identified Go2-W whose delivered configuration matches V1.1's startup arrangement, an approved already charged battery, Unitree Go app/account, and an operator trained in the delivered controller/app's stop action. The manual gives a binding menu but no full handheld button table; do not assume the consumer Go2 remote stop combination. Confirm that method from the supplied controller instructions before power. Use a dry level area with traction, 5–35 °C, at least 2 m clearance, and clear wheel/joint motion space. This is an automatic-startup observation, not a motion-free test. [Go2-W V1.1 pp. 2, 7–11](https://marketing.unitree.com/article/en/Go2-W/User_Manual.html)

1. With the pack off, check labels, latch it switch-up and set the exact wheeled horizontal posture shown on p. 8. Do not lift or reposition after power-on.
2. Confirm the supplied battery's instruction agrees with the Go2-W manual. Its prose specifies one short press followed by a hold of at least 2 s. If pack instructions differ or the part cannot be identified, stop and obtain the revision-specific instruction.
3. Observe startup from outside the motion envelope. Page 8 describes green flashing, then steady green after approximately two minutes with the body horizontal. Abnormal posture, rolling, slipping or fault lights are failure criteria; do not command a gait to correct them.
4. Install **Unitree Go** from the [official download hub](https://www.unitree.com/app/go2/). Sign in, enable Bluetooth/app permissions, keep the phone nearby, choose **Home → Add robot**, select the unit matched to the physical label and enter the robot information. A discovery name beginning `Go2_` alone does not prove wheeled identity.
5. Choose the manual's AP/hotspot path or a known router Wi-Fi path. In AP mode connect the phone's Wi-Fi settings to the robot hotspot established in the binding flow, then return to the app. For router mode use the intended router credentials. Do not reuse screenshot SSIDs, remote codes or invented passwords.
6. Confirm the intended robot's connected state, battery/status and camera view when available, and record app/robot firmware, LiDAR label and module/payload BOM. Complete the built-in tutorial before later manual motion; do not activate autonomous routes, recovery, calibration or wheel tests as part of this result.

**Expected result:** the intended Go2-W is bound to the authorized account with a live connection and normal steady-green startup state. In Go2-W V1.1 p. 4, green means powered on; unlike the consumer Go2 table it does **not** establish avoidance-enabled status. Camera reception verifies that path only, not LiDAR decoding or wheel calibration. No such result was observed on hardware here.

**If this check fails:** safely power down using the matched instructions, then distinguish startup-posture, app-permission, AP/router and hardware-fault causes below. Do not unbind someone else's account or use blind calibration. To finish a normal session, use the trained low-down action on level ground, confirm prone/damping, then follow V1.1 p. 12's power sequence and confirm lights out before handling/storage. Cutting power while standing can cause a fall.

### Prerequisites for the separate developer checkpoint <a href="#prerequisites-for-the-separate-developer-checkpoint" id="prerequisites-for-the-separate-developer-checkpoint"></a>

The following subscription is only for an **already commissioned Go2-W** with confirmed firmware/SDK pairing and a provisioned host network. V1.1 establishes the physical RJ45 interface; the now-read Go2-W quick start specifies the robot endpoint and example external-host subnet below. Exact delivered DDS/service and firmware/API pairing still requires confirmation before a device session. Use an existing verified Python environment at the pinned commit; no installation/build, ROS setup, device communication or firmware update was performed here.

### First working result: bounded status subscription <a href="#first-working-result-bounded-status-subscription" id="first-working-result-bounded-status-subscription"></a>

1. In the supplier-approved stationary setup, confirm that the app/controller identifies Go2-W and displays battery/status without initiating a gait, follow mode, navigation or recovery motion. Preserve the label, firmware and network settings in the commissioning record.
2. Select the actual Linux interface attached to the provisioned robot network. In the command below, replace `ROBOT_INTERFACE` with that exact name; it is a placeholder, not an interface or IP to copy.
3. Save the following original example as `read_go2w_status.py`. It uses the topic/type pair in the reviewed Go2-W source and the official subscriber API. It reads at most one `LowState_` sample within ten seconds. It has no command publisher or motion client.

```python
import sys
from unitree_sdk2py.core.channel import ChannelFactoryInitialize, ChannelSubscriber
from unitree_sdk2py.idl.unitree_go.msg.dds_ import LowState_

if len(sys.argv) != 2:
    raise SystemExit("Usage: python3 read_go2w_status.py ROBOT_INTERFACE")
ChannelFactoryInitialize(0, sys.argv[1])
sub = ChannelSubscriber("rt/lowstate", LowState_)
sub.Init()
try:
    msg = sub.Read(10.0)
    if msg is None:
        raise SystemExit("No Go2-W state in 10 seconds; stop and check provisioning.")
    if len(msg.motor_state) < 16:
        raise SystemExit("State has fewer than 16 motor slots; verify type/firmware.")
    print("tick:", msg.tick)
    print("power_v:", msg.power_v, "power_a:", msg.power_a)
    for name, index in (("FR_w", 12), ("FL_w", 13), ("RR_w", 14), ("RL_w", 15)):
        print(name, "q:", msg.motor_state[index].q, "dq:", msg.motor_state[index].dq)
finally:
    sub.Close()
```

```bash
python3 read_go2w_status.py ROBOT_INTERFACE
```

4. Compare the sample with the app battery/status and the known stationary state. A decodable packet and a 16-slot array do not prove correct joint calibration, wheel direction or package identity. Take a second bounded sample only if necessary to confirm that `tick` advances. Preserve actual output and firmware/SDK/interface records without publishing serials or credentials.

**Expected result:** one decoded low-state sample containing `tick`, `power_v`, `power_a` and four wheel slots; then the subscriber closes. No motion command is sent. This is expected behavior from source inspection, not observed robot output. The firmware-to-message contract and wheel field units/signs must still be confirmed for the delivered unit. The IDL has 20 motor slots; capacity does not prove 20 physical joints or that wheel calibration is correct. [Go2-W topic/type usage](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/example/go2w/low_level/go2w_stand_example.py), [subscriber API](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/unitree_sdk2py/core/channel.py)

**If this check fails:** close the subscriber. Verify the exact platform and firmware, then SDK snapshot/type, selected physical network interface and supplier-defined network configuration. An app connection is not proof that DDS traffic reaches the development host. Do not release the motion service, run a stand example or change robot firmware to make status appear.

### Model-specific controller functions and terrain boundaries <a href="#model-specific-controller-functions-and-terrain-boundaries" id="model-specific-controller-functions-and-terrain-boundaries"></a>

The [Go2-W Operation Guide](https://doc-cdn.unitree.com/15/301/en/15_301_en) says power-on can automatically stand the robot and starts in low-speed sport mode. Establish clearance before power-on; app connection is not a no-motion guarantee. In this article, left-stick fore/aft and lateral inputs request translation; right-stick fore/aft changes the look/posture direction and lateral input turns the robot. Confirm the supplied remote and firmware before using these mappings.

| Documented combination              | Meaning in this Go2-W article                                                                                                                    |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| L2 + B                              | Damping, described by Unitree as a soft emergency stop. It is a software control state, not independently rated power isolation.                 |
| L2 + X                              | Rollover/recovery motion; not a diagnostic or stop.                                                                                              |
| L2 + A                              | First standing joint lock; a second selection lies down. Confirm actual state before a transition.                                               |
| L2 + START                          | High-speed motion mode.                                                                                                                          |
| Right direction + START             | Terrain mode.                                                                                                                                    |
| R1 + X                              | Climbing mode.                                                                                                                                   |
| L1 + A, then R2 held                | Prepares inversion; holding R2 inverts, releasing it returns to normal.                                                                          |
| L1 + A, then direction combinations | Left/up or right/up requests rotating inversion; down returns normally; up can maintain inversion. These are moving maneuvers, not setup checks. |

High-speed mode is described for small obstacles no higher than 5 cm and not for stairs; the source discourages rushing down stairs and says speed reduces on slopes. Terrain mode trades speed for irregular ground and stairs; lateral passage over obstacles can wear the wheels. Climbing needs a regular rectangular wall/platform, facing it directly, at least 15 cm wall width; the source ceiling is 70 cm, but it recommends no more than 50 cm because of body collision risk. Contact by a person can be misinterpreted as a wall. Inversion does not support lateral travel and the article limits sustained inversion to one minute because of the wheel load. These statements bound specialized modes; they are not activities required for commissioning. [Operation Guide](https://doc-cdn.unitree.com/15/301/en/15_301_en)

### App binding and network paths <a href="#app-binding-and-network-paths" id="app-binding-and-network-paths"></a>

The [Go2-W binding article](https://doc-cdn.unitree.com/15/735/en/15_735_en) uses the Unitree Go app: register/sign in, add the intended powered robot over phone Bluetooth, confirm identity and set its displayed information. AP mode creates/selects the robot hotspot and an eight-digit password; the phone joins that hotspot and then completes the app prompt. Wi-Fi mode instead provisions an existing router and returns to the home screen after connection. Keep credentials private. App service-status switches can change running services; a successful image or sensor panel is evidence of that app path, not DDS host connectivity, correct wheel calibration or control ownership.

The [developer quick start](https://doc-cdn.unitree.com/15/276/en/15_276_en) recommends Ubuntu 20.04 on an external PC; it does not support Mac/Windows development or development on the robot’s built-in computer in that tutorial. The example Ethernet host is **192.168.123.222** on the robot subnet; the robot is **192.168.123.161**, so do not assign `.161` to the PC. The ROS article uses `.99` as another example host, not a second robot address. Use the actual connected interface name, not an example’s `enxf8e43b808e06`. Reachability alone does not prove DDS discovery, firmware support or a valid robot state. [Quick Start](https://doc-cdn.unitree.com/15/276/en/15_276_en), [ROS2 interface](https://doc-cdn.unitree.com/15/285/en/15_285_en), [Debugging Specification](https://doc-cdn.unitree.com/15/279/en/15_279_en)

The quick start describes installing SDK2 into a default or selected prefix and separately building its examples; its screenshots and executable names can lag a repository revision. No installation or build was done here. Its `go2w_sport_test` menu includes motions, and selecting damping/stand/recovery is an active request. Use the bounded subscriber below as the first developer checkpoint after network and firmware provisioning; no service switch is needed merely to receive state.

### Offline perception result before a device session <a href="#offline-perception-result-before-a-device-session" id="offline-perception-result-before-a-device-session"></a>

The receive-only SDK checkpoint above is conditional on a commissioned robot and provisioned environment. This separate **original offline** exercise needs only an existing Python 3 interpreter. Save the complete block as a local file and run it locally; it imports no Unitree code, opens no network or serial connection, and publishes no request. It turns one synthetic two-cell map into a single valid point, following the source’s indexing and empty-cell convention. [Delegated LiDAR chapter](https://doc-cdn.unitree.com/6/51/en/6_51_en)

```python
"""Original offline height-map exercise; no Unitree imports or device access."""
from math import isfinite


def points(record):
    width, height = record['width'], record['height']
    if type(width) is not int or type(height) is not int:
        raise ValueError('Integer dimensions required')
    if width <= 0 or height <= 0 or width * height > 65536:
        raise ValueError('Invalid or excessive map dimensions')
    if record['frame_id'] != 'odom':
        raise ValueError('Expected source odom frame')
    resolution = float(record['resolution'])
    origin = tuple(float(v) for v in record['origin'])
    if len(origin) != 2 or not all(isfinite(v) for v in origin):
        raise ValueError('Finite two-dimensional origin required')
    if not isfinite(resolution) or resolution <= 0:
        raise ValueError('Finite positive resolution required')
    values = record['data']
    if len(values) != width * height:
        raise ValueError('Map shape does not match data length')
    result = []
    for index, raw in enumerate(values):
        z = float(raw)
        if z == 1.0e9 or not isfinite(z):
            continue
        ix, iy = index % width, index // width
        result.append((origin[0] + ix * resolution,
                       origin[1] + iy * resolution, z))
    return result


if __name__ == '__main__':
    synthetic = dict(frame_id='odom', width=2, height=1,
                     resolution=0.1, origin=(1.0, 2.0),
                     data=(0.5, 1.0e9))
    result = points(synthetic)
    print('OFFLINE map points:', result)
    print('Synthetic only; freshness and robot operation unverified')
```

Expected output is `OFFLINE map points: [(1.0, 2.0, 0.5)]`, followed by the explicit synthetic/unverified statement. The missing second point is the source’s empty-cell sentinel. This checks mathematical interpretation only; it does not verify the running LiDAR model, camera, map service, obstacle avoidance or a physical route. Before using a captured map, additionally validate source timestamp/clock, local receipt age, message progression, frame transforms and the delivered service configuration.

### Developer session record and stopping conditions <a href="#developer-session-record-and-stopping-conditions" id="developer-session-record-and-stopping-conditions"></a>

Keep an explicit record of Go2-W nameplate/package, firmware and service versions, SDK commits, external host/interface/IP, actual running controller, message type and topic, battery/charger and sensor/payload identity. Start with a bounded subscriber and independently observed app state. A fresh message should have plausible finite fields, advancing local receipt sequence and a consistent tick/clock; a stationary wheel need not have changing position. Preserve unknown enum bits instead of dropping them.

Do not switch off motion services, select a gait, reset calibration or send a low-level packet to diagnose a missing subscription. For invalid type/shape, nonfinite values, stale reception, unexplained faults or conflicting control ownership, close the observer and resolve the cause before further development. The bounded subscriber’s closure releases only the observer. For a later authorized control session, stopping must be planned independently of host cleanup, a final UDP/DDS message, an example’s timeout comment or a terminal success label.

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

### What do Go2-W lights and startup faults mean? <a href="#what-do-go2-w-lights-and-startup-faults-mean" id="what-do-go2-w-lights-and-startup-faults-mean"></a>

V1.1 p. 4 maps flashing green to boot, steady green to powered-on, slow blue to motor/IMU calibration, slow yellow to low battery with possible automatic crouch within ten minutes, slow red to system/boot/hardware abnormality, fast red to failed motor/IMU calibration and steady white to the lamp. End a low-battery session safely at the warning; ten minutes is not a guaranteed reserve. Do not transfer consumer Go2's steady blue/yellow/purple mode meanings to this table. [Exact Go2-W indicator page](https://marketing.unitree.com/article/en/Go2-W/User_Manual.html)

For a slow-red failure to stand, V1.1 p. 13 first directs checking startup placement and restarting; power down before repositioning. If it persists, preserve the app alarm and obtain support. For abnormal posture or repeated falls, the manual says the robot is factory calibrated and to consult Unitree before joint/IMU recalibration. Its menu **Settings → Data → Machine Dog → imu Information → Calibration** is a location reference, not a command to recalibrate a normal unit. For a stopped LiDAR, inspect the app alarm and obstruction from a safe state; do not touch a powered scanner even though the manual mentions nudging it.

### Why will the app or handheld not connect? <a href="#why-will-the-app-or-handheld-not-connect" id="why-will-the-app-or-handheld-not-connect"></a>

Check phone Bluetooth and Unitree Go permission, then the selected connection path: AP requires the robot's actual hotspot; router Wi-Fi requires the intended network/external connection; 4G requires an available supported data service. V1.1 p. 11 gives **Settings → Remote Control Settings**, switch on remote control and enter the **actual** controller code. The screenshot code is not universal. The supplied controller revision determines its link LEDs and stop controls.

For an authorized ownership transfer, p. 10 gives **Home → Settings → Robot Settings → Switch Connection → Unbind**; it removes app control and allows rebinding. Do not use unbinding as a casual reset, and seek official assistance for a lost account. Offline voice is described on p. 11 as Chinese; the manual's phone-app English route does not establish an offline English voice API.

### Why are wheels missing or mapped as leg motors? <a href="#why-are-wheels-missing-or-mapped-as-leg-motors" id="why-are-wheels-missing-or-mapped-as-leg-motors"></a>

Confirm the robot is Go2-W and the application uses the wheel-specific constants. The leg-only map covers 0–11; Go2-W adds 12–15. Then check the exact firmware/type contract and topic before interpreting values. Array length alone cannot distinguish unused slots from active motors. Stop before commanding a wheel with a leg control policy. [Pinned wheel map](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/example/go2w/low_level/unitree_legged_const.py)

### Why does selecting `get_state` in the high-level example do nothing? <a href="#why-does-selecting-get_state-in-the-high-level-example-do-nothing" id="why-does-selecting-get_state-in-the-high-level-example-do-nothing"></a>

The reviewed `go2w_sport_client.py` lists that menu option without an implemented dispatch branch. This is a source-level observation, not a robot failure. Use the bounded subscriber above after provisioning is verified. Do not select `recovery`, `stand_up` or `move` as a diagnostic substitute.

### Why does the app connect but DDS times out? <a href="#why-does-the-app-connect-but-dds-times-out" id="why-does-the-app-connect-but-dds-times-out"></a>

First compare the SDK's selected interface with the supplied robot network instructions; then check domain 0 and the exact `unitree_go` type against the firmware. Have the network administrator check DDS discovery/multicast permissions if applicable to that configuration. Keep firewall and routing changes specific to supplier instructions; no global disablement or guessed address is part of this guide.

### Is a Go2 Air/Pro battery, remote or manual interchangeable? <a href="#is-a-go2-airpro-battery-remote-or-manual-interchangeable" id="is-a-go2-airpro-battery-remote-or-manual-interchangeable"></a>

Interchangeability was not established. Go2-W V1.1 now supplies its own startup, interfaces and binding procedure; use those. Similar voltage or a shared app/library name is insufficient to transfer battery protections, charging, handheld button mappings or wheel stop behavior. Require exact Go2-W/part-number applicability for the supplied battery and controller manuals.

### Can the robot recover or roll back firmware through SDK2? <a href="#can-the-robot-recover-or-roll-back-firmware-through-sdk2" id="can-the-robot-recover-or-roll-back-firmware-through-sdk2"></a>

No supported Go2-W firmware recovery procedure was verified. The dock drawing labels a service recovery control, but a label is not a procedure. `RecoveryStand()` is a motion API, not firmware recovery. OTA presence does not establish a supported downgrade, bootloader image, recalibration procedure or factory reset. If an update or boot fails, retain the displayed error, firmware versions and supplier-approved diagnostic logs, then use the exact model's authorized recovery procedure. Do not flash a Go2 image or attempt undocumented service credentials.

### Can U5 thermal readings be used directly for inspection decisions? <a href="#can-u5-thermal-readings-be-used-directly-for-inspection-decisions" id="can-u5-thermal-readings-be-used-directly-for-inspection-decisions"></a>

The store lists a thermal payload, but no reviewed payload manual establishes emissivity handling, radiometric output, accuracy conditions or calibration traceability. Identify the actual imager/gimbal and obtain its calibration and SDK documentation first. The U5 listing explicitly excludes the D1 arm; do not infer its compatibility from general platform expansion images.

### Portal fault aggregation and field-level diagnostics <a href="#portal-fault-aggregation-and-field-level-diagnostics" id="portal-fault-aggregation-and-field-level-diagnostics"></a>

The [Fault Services article](https://doc-cdn.unitree.com/15/284/en/15_284_en) distinguishes a **fault source** from a **bitmask at that source**. `rt/errorlist` carries a `std_msgs::msg::dds_::String_` JSON payload with `errors` rows `[timestamp, source, mask]`. The WebRTC component aggregates underlying sources; an empty or absent aggregate is not proof that every sensor/drive is healthy. Preserve the original timestamp, source and complete mask, and compare underlying topics. The article does not establish a universal timestamp unit, clock origin or retained-history guarantee.

| Source              | Underlying evidence                                                        | Bits documented in the Go2-W chapter                                                                                                                                                                             |
| ------------------- | -------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 100                 | `rt/lf/lowstate`, `bit_flag`                                               | 0x40 MCU communication; 0x80 motor communication; 0x10 battery communication; 0x02 power/distribution switch abnormal. Remote 0x20 and operation-command 0x01 are marked abandoned/obsolete in this fault table. |
| 200                 | Low-state fan word 3                                                       | 0x01 left-rear fan (marked abandoned), 0x02 right-rear, 0x04 front blockage.                                                                                                                                     |
| `300+(leg*3+motor)` | Motor `reserve[0]`; reserve\[1] is contemporaneous communication frequency | 0x01 overcurrent, 0x02 overvoltage, 0x04 drive hot, 0x08 undervoltage, 0x10 winding hot, 0x20 encoder fault, 0x100 interrupted motor communication.                                                              |
| 400                 | `rt/utlidar/lidar_state`, `error_state`                                    | 0x01 abnormal speed, 0x02 point-cloud abnormality, 0x04 serial-data abnormality.                                                                                                                                 |

The leg-source formula documents twelve leg joints; it does not separately establish fault-source numbering for the four wheels. Retain unrecognized wheel/source values and ask for the delivered firmware schema. This aggregate motor mask also differs from a standalone GO-M8010-6’s three-bit serial enum and an IM6014’s wider mask; shared manufacturer names do not make fault meanings interchangeable.

The [Basic Services chapter](https://doc-cdn.unitree.com/15/282/en/15_282_en) additionally exposes bit 0x04 as **1 not charging / 0 charging**, winder current, board/charging temperatures, main power voltage/current and per-motor lost counters. Its older timeout comments and the fault table’s obsolete labels describe different documentation generations. A stale low-state message can repeat a perfectly plausible zero fault mask; record receipt age and progressing `tick` before drawing a conclusion. No automatic fault-clear, power-cycle or firmware update is prescribed by this diagnostic reference.

On abnormal current, heat, communication or encoder state, stop further application progression under the commissioned stop plan and retain raw evidence. Loss of DDS cannot guarantee delivery of a last `StopMove` or damping request. Load support, external isolation and the model-matched manufacturer recovery procedure remain separate from decoding a fault. Service 5201/5202 or generic RPC errors are request outcomes, not replacements for these hardware masks.

### Source-example traps to resolve before development <a href="#source-example-traps-to-resolve-before-development" id="source-example-traps-to-resolve-before-development"></a>

The portal’s Python page labels `lowlevel_control.py` a status reader and then uses the **same path** for an active joint-control example. It describes a calf torque and hip position target. Never treat that filename or the word “Status” as evidence that execution is receive-only. Its high-level script performs stand-up/down; VUI cycles volume/light; generic DDS and camera programs have their own interfaces and dependencies. Old `/example/high_level` paths may differ from the pinned model-specific tree. Use source inspection, not a tutorial label, to decide what a program transmits. [Python Services](https://doc-cdn.unitree.com/15/286/en/15_286_en)

The generic [DDS case](https://doc-cdn.unitree.com/15/287/en/15_287_en) publishes `TopicHelloWorld` once per second and demonstrates subscriber close/reopen; that is custom test data, not robot state or firmware validation. Its separate SportClient loop repeatedly sends forward movement. The ROS low-level example moves a leg and the ROS sport example starts walking after a delay. Neither is part of the first receive-only result below. [DDS Communication](https://doc-cdn.unitree.com/15/287/en/15_287_en), [ROS2 Services](https://doc-cdn.unitree.com/15/285/en/15_285_en)

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

| Resource                                                         | Purpose and exact scope                                                                                | Official link and access state                                                                                                                                                                                                                                                                                                                                         |
| ---------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Go2-W product page                                               | Current platform specifications and original image                                                     | [Read manufacturer page](https://www.unitree.com/go2-w/)                                                                                                                                                                                                                                                                                                               |
| Go2-W User Manual V1.1                                           | 16 original page images; model-specific startup, interfaces, binding, diagnostics and revision history | [Read exact manual](https://marketing.unitree.com/article/en/Go2-W/User_Manual.html), OCR-assisted and critical figures visually checked                                                                                                                                                                                                                               |
| Python SDK snapshot                                              | Dependencies and interface model; README paths may lag repository layout                               | [Pinned README](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/README.md), source read                                                                                                                                                                                                                           |
| Go2-W high-level example                                         | Inspect implemented commands and menu limits                                                           | [Exact source](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/example/go2w/high_level/go2w_sport_client.py), read; contains active controls                                                                                                                                                                      |
| Go2-W low-level example and motor constants                      | Verify actual topic/type and wheel indices                                                             | [Low-level source](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/example/go2w/low_level/go2w_stand_example.py), [constants](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/example/go2w/low_level/unitree_legged_const.py); read, not a first-run command |
| Channel implementation                                           | Subscriber initialization, read timeout and close semantics                                            | [Pinned API source](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/unitree_sdk2py/core/channel.py), read                                                                                                                                                                                                         |
| Developer network quick start                                    | External Ubuntu PC, robot .161 and a separate nonconflicting host                                      | [Actual Go2-W article](https://doc-cdn.unitree.com/15/276/en/15_276_en), actual text read                                                                                                                                                                                                                                                                              |
| Legacy / related Go2 quick start                                 | Retained source reference from the earlier published page                                              | [General Go2 quick start](https://support.unitree.com/home/en/developer/Quick_start); this is a related Go2 reference, not the primary Go2-W procedure, and its instructions are not transferred to Go2-W                                                                                                                                                              |
| Exact battery and handheld manuals for the delivered Go2-W parts | Charging, storage, protection limits and controller-specific stop buttons                              | Go2-W V1.1 covers robot operation and binding; separate part-specific battery/remote applicability remains unverified                                                                                                                                                                                                                                                  |
| Go2-W schematic, recovery and CAD/calibration                    | External integration and service                                                                       | Interface drawings and STEP/URDF links now documented; archive contents, exact polarity/shared power budget and robot-firmware recovery remain unresolved. Shared dock compute recovery is a conditional source reference only.                                                                                                                                        |
| U1–U5 package and U5 payload manuals                             | Delivered package differences and payload interfaces                                                   | No exact OEM package manual read; required before payload operation                                                                                                                                                                                                                                                                                                    |

The 16-page Go2-W manual is indexed below with original engineering paraphrases. The four consumer Go2 manuals do not establish additional Go2-W battery/remote applicability. No full transcript or manual facsimile is republished.

### Go2-W User Manual V1.1: complete source-page index <a href="#go2-w-user-manual-v11-complete-source-page-index" id="go2-w-user-manual-v11-complete-source-page-index"></a>

Original Unitree source: [Go2-W User Manual V1.1](https://marketing.unitree.com/article/en/Go2-W/User_Manual.html). Page links open the OEM originals; summaries below are original engineering interpretation, not a transcript.

| Source page | Section and engineering use                                                                                                                                            | Original                                                                                                |
| ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| 1           | **Cover / version:** Establish the exact wheeled V1.1 source independently from leg-only Go2 manuals.                                                                  | [OEM p. 1](https://doc-cdn.unitree.com/static/2026/6/4/1169ac28163c4866a738fdd1bc0407ea_2482x3509.png)  |
| 2           | **Safety / wheel traction / environment:** Dry 5–35 °C use, 2 m clearance, line of sight and suitable traction; no powered lifting or back-loaded rolls.               | [OEM p. 2](https://doc-cdn.unitree.com/static/2026/6/4/794e4a5e9f684474885eb2069e7ca3b3_2481x3509.png)  |
| 3           | **Architecture / L2 / parts / edition matrix:** Sixteen-DOF wheel platform, L2 revision and expansion hardware; identify delivered sensors and compute.                | [OEM p. 3](https://doc-cdn.unitree.com/static/2026/6/4/6bb51e66fdf24244b8030e20a907bb0c_2481x3509.png)  |
| 4           | **Status / app / development / rear panel:** Go2-W green means powered on; rear 28.8 V output and RJ45 roles differ from a supply input.                               | [OEM p. 4](https://doc-cdn.unitree.com/static/2026/6/4/f158c894ab594bbe92177155fd942cf1_2481x3509.png)  |
| 5           | **Ethernet / SBUS / compute table:** Panel-view SBUS is NC/GND/SBUS with no power; 16GB heading versus 8GB memory is unresolved.                                       | [OEM p. 5](https://doc-cdn.unitree.com/static/2026/6/4/74b6a5b34bec4a9398b0c9e0fd5ce50d_2481x3509.png)  |
| 6           | **Expansion dock figure:** Keep dock input ratings and accessory outputs separate from robot power; connector pin details remain incomplete.                           | [OEM p. 6](https://doc-cdn.unitree.com/static/2026/6/4/fa574f08f2874cc0a5468f2571f8a8c4_2482x3509.png)  |
| 7           | **Inspection / pack insertion:** Use powered-off label checks, side insertion switch-up and latch confirmation.                                                        | [OEM p. 7](https://doc-cdn.unitree.com/static/2026/6/4/cd5d9e8cf23942bba8cac6cefe1517d6_2482x3509.png)  |
| 8           | **Wheeled posture / startup:** Use original wheel-contact and belly-pad figure; prose specifies short press then hold at least 2 s.                                    | [OEM p. 8](https://doc-cdn.unitree.com/static/2026/6/4/0e82698010004c808b3d16654431bb64_2481x3509.png)  |
| 9           | **App binding / Bluetooth / AP or router:** Match the physical robot and intended network; screenshot names are not defaults.                                          | [OEM p. 9](https://doc-cdn.unitree.com/static/2026/6/4/5adf9e9eb4b946a28fd6cabb1011d8e2_2481x3509.png)  |
| 10          | **Unbinding / permissions / lost account:** Owner-authorized unbinding changes app control; permissions and official account support precede resets.                   | [OEM p. 10](https://doc-cdn.unitree.com/static/2026/6/4/0d95b30a10af40ffa469b9572813cff7_2481x3509.png) |
| 11          | **App / voice / handheld pairing:** Complete tutorial; offline speech is Chinese and remote binding uses Settings → Remote Control Settings.                           | [OEM p. 11](https://doc-cdn.unitree.com/static/2026/6/4/df1804d7545947b5bf4d99657e3c8b10_2481x3509.png) |
| 12          | **Low-down / power-off / storage:** Confirm prone/damping before power removal; resolve reversed figure-caption wording against supplied instructions.                 | [OEM p. 12](https://doc-cdn.unitree.com/static/2026/6/4/c823e11d3cd74cfdb0d5793054b5cab1_2482x3509.png) |
| 13          | **Startup / network / posture / scanner faults:** Check placement and connection route first; consult support before recalibration, avoid powered scanner handling.    | [OEM p. 13](https://doc-cdn.unitree.com/static/2026/6/4/d2122e4739804663a268e3cea0b9120a_2482x3509.png) |
| 14          | **Cautions / terrain / wear / performance conflicts:** Air remnants and conflicting speed/slope/step text prevent treating these as reconciled Go2-W operating maxima. | [OEM p. 14](https://doc-cdn.unitree.com/static/2026/6/4/4c971bf7059a491e83c1e44828615c31_2481x3508.png) |
| 15          | **Disclaimer / service boundaries:** Preserve OEM use/service restrictions and original terms without inventing certification or warranty.                             | [OEM p. 15](https://doc-cdn.unitree.com/static/2026/6/4/30c024eeb0a640d888b82851f7638719_2481x3508.png) |
| 16          | **Revision history / L1 to L2:** History explicitly changes L1 to L2 but prints 2016 for V1.1 before a 2024 V1.0; retain the date conflict.                            | [OEM p. 16](https://doc-cdn.unitree.com/static/2026/6/4/94166fc39c4d47c0934ff296ae254809_2481x3508.png) |

### Additional official resources observed in the portal <a href="#additional-official-resources-observed-in-the-portal" id="additional-official-resources-observed-in-the-portal"></a>

* [Go2-W simplified STEP archive](https://oss-global-cdn.unitree.com/static/edf4771b7ed540159bff8b4a86bb6c74.zip) and [Go2-W URDF archive](https://oss-global-cdn.unitree.com/static/cf789213ba354db5a94fe10946bd7c32.zip), listed by [Obtain SDK](https://doc-cdn.unitree.com/15/275/en/15_275_en). Contents, mesh calibration, license and build compatibility not inspected.
* [Rear electrical-interface drawing](https://doc-cdn.unitree.com/static/2024/9/3/e1439bb85b6048b2a324a85517ddc1b8_3773x1458.png) and [back mounting-hole drawing](https://doc-cdn.unitree.com/static/2024/9/3/f444e6554eea470ea1f52037473df248_2622x1542.png), linked by About Go2-W; use the exact shown view and delivered revision.
* [Expansion dock figure](https://doc-cdn.unitree.com/static/2024/5/14/7ca51de5cdc34b63bd6ff3a7ec74216b_1814x396.png), Unitree’s original attributed hardware reference; ratings and conflicts are interpreted above, not inferred from appearance.

These selected links retain source attribution without republishing a complete manual or image collection. SDK source licensing does not automatically license manuals, photos, archives, payload firmware or third-party media.

### Complete portal source coverage index <a href="#complete-portal-source-coverage-index" id="complete-portal-source-coverage-index"></a>

The following are actual article bodies read on 24 November 2026. These entries map source headings to original functional explanations above; file/video/archive targets remain linked resources unless separately evidenced.

| Read article                                                                            | Functional coverage                                                                                                                                                                                      |
| --------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [About Go2-W](https://doc-cdn.unitree.com/15/272/en/15_272_en)                          | Platform/optional accessory ratings, sensor and camera modes, revision/capability conflicts; see **Portal hardware specification and accessory scope**.                                                  |
| [Operation Guide](https://doc-cdn.unitree.com/15/301/en/15_301_en)                      | Controller combinations, power-on movement, terrain/climbing/inversion constraints; see **Model-specific controller functions and terrain boundaries**.                                                  |
| [Application Development](https://doc-cdn.unitree.com/15/273/en/15_273_en)              | Development navigation/delegation; functional destination chapters read individually; see **Portal service architecture and source versions**.                                                           |
| [SDK Concepts](https://doc-cdn.unitree.com/15/274/en/15_274_en)                         | SDK overview explicitly delegates Go2 architecture; see **Portal service architecture and source versions**.                                                                                             |
| [Obtain SDK](https://doc-cdn.unitree.com/15/275/en/15_275_en)                           | SDK2 plus STEP/URDF links; archive contents not inspected; see **Portal service architecture and source versions**.                                                                                      |
| [Quick Start](https://doc-cdn.unitree.com/15/276/en/15_276_en)                          | External Ubuntu PC, Ethernet addresses/interface, install/build separation and active test menu; see **App binding and network paths**.                                                                  |
| [App\_binding](https://doc-cdn.unitree.com/15/735/en/15_735_en)                         | Account/Bluetooth identity, AP versus router Wi-Fi, services/data panels; see **App binding and network paths**.                                                                                         |
| [Payload](https://doc-cdn.unitree.com/15/1285/en/15_1285_en)                            | Dock input/output, network/USB roles and supply/link-rate conflicts; see **Portal electrical and coordinate details**.                                                                                   |
| [Software Interface Services](https://doc-cdn.unitree.com/15/277/en/15_277_en)          | DDS/RPC/video split and explicit shared-service delegation; see **Portal service architecture and source versions**.                                                                                     |
| [DDS Services Interface](https://doc-cdn.unitree.com/15/280/en/15_280_en)               | Factory/publisher/subscriber lifecycle, queue/timestamps, RPC/errors/leases and pin mismatches; see **Portal service architecture and source versions**.                                                 |
| [RobotStateClient Interface](https://doc-cdn.unitree.com/15/281/en/15_281_en)           | Service list/switch/reporting, error codes, version-specific signatures and identifiers; see **Service status and control ownership**.                                                                   |
| [Basic Services Interface](https://doc-cdn.unitree.com/15/282/en/15_282_en)             | All message groups, wheel map, command effects, type/IDL defects, state/control direction; see **Low-level state, command layout and source defects**.                                                   |
| [Sports Services Interface](https://doc-cdn.unitree.com/15/283/en/15_283_en)            | All ten documented functions, preconditions, mode limits and absent pinned methods; see **Go2-W high-level motion reference**.                                                                           |
| [Fault Services Interface](https://doc-cdn.unitree.com/15/284/en/15_284_en)             | Aggregate/source/masks, obsolete bits, fan/motor/LiDAR faults and freshness limits; see **Portal fault aggregation and field-level diagnostics**.                                                        |
| [ROS2 Services Interface](https://doc-cdn.unitree.com/15/285/en/15_285_en)              | OS/middleware/build order/environment, state and command topics, examples and RViz frames; see **ROS2 and Python integration reference**.                                                                |
| [Python Services Interface](https://doc-cdn.unitree.com/15/286/en/15_286_en)            | Python dependencies/middleware resolution; all example categories and unsafe status label; see **ROS2 and Python integration reference**.                                                                |
| [Case Reference](https://doc-cdn.unitree.com/15/278/en/15_278_en)                       | Case-reference introduction; actual linked cases read individually; see **Source-example traps to resolve before development**.                                                                          |
| [DDS Communication](https://doc-cdn.unitree.com/15/287/en/15_287_en)                    | Custom HelloWorld topic, subscriber reopen and distinct active SportClient loop; see **Source-example traps to resolve before development**.                                                             |
| [High Motion Control](https://doc-cdn.unitree.com/15/288/en/15_288_en)                  | Menu dispatch/retained action, request outcome and gait/GetState source-version issues; see **Go2-W high-level motion reference**.                                                                       |
| [Basic\_motion\_control](https://doc-cdn.unitree.com/15/289/en/15_289_en)               | Ownership, receive gate weakness, four control phases, CRC and persistent-command effects; see **What the wheel-control demonstration actually does**.                                                   |
| [Debugging Specification](https://doc-cdn.unitree.com/15/279/en/15_279_en)              | Ethernet PC-to-robot diagnostic connection figure only; no hidden recovery content; see **App binding and network paths**.                                                                               |
| [Expansion Dock Configuration](https://doc-cdn.unitree.com/6/110/en/6_110_en)           | Explicit Go2-W service packages; dock address/display/configuration conflicts and model-bounded update/repair/NVMe recovery reference; see **Additional dock-package references and recovery boundary**. |
| [VuiClient Interface](https://doc-cdn.unitree.com/6/75/en/6_75_en)                      | VUI get/set/ranges/error and source pin; see **Delegated Go2 volume, image and LiDAR services**.                                                                                                         |
| [LiDAR Services Interface](https://doc-cdn.unitree.com/6/51/en/6_51_en)                 | Cloud/map/range/switch topics, fields, indexing/frames/dependencies, parser and visualization limits; see **Delegated Go2 volume, image and LiDAR services**.                                            |
| [Multimedia Services Interface](https://doc-cdn.unitree.com/6/53/en/6_53_en)            | JPEG RPC, multicast RTP/H264 pipeline, dependencies/backends and capture/freshness limits; see **Delegated Go2 volume, image and LiDAR services**.                                                       |
| [SLAM and Navigation Services Interface](https://doc-cdn.unitree.com/6/111/en/6_111_en) | Explicit Go2\_W configurations/speed; seven navigation APIs, six topics, JSON units/frames, completion, limits and package ownership; see **Go2-W package-scoped SLAM and navigation reference**.        |
| [Aruco Recharge Service Interface](https://doc-cdn.unitree.com/6/298/en/6_298_en)       | Go2 NX applicability versus Go2-W archive; marker parameters, active recharge state/retry contracts and ABI boundaries; see **Recharge package label versus qualified Go2-W installation**.              |

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

* Unitree, [Go2-W product page](https://www.unitree.com/go2-w/): current public platform table, footnotes and original image; reviewed 24 November 2026, no revision identifier on the page.
* Unitree, [Go2-W User Manual V1.1](https://marketing.unitree.com/article/en/Go2-W/User_Manual.html): all 16 page images reviewed with OCR assistance; pp. 4–6, 8 and 16 original figures/tables visually checked. The printed revision date and compute/performance contradictions are retained explicitly.
* Unitree Robotics, [Python SDK](https://github.com/unitreerobotics/unitree_sdk2_python/tree/814556d15970dd2ecf1c9984e845ca02ab07e206): reviewed README, subscriber implementation, message definition, Go2-W examples and motor map at the pinned commit.
* OpenELAB U1–U5 catalog and observed product links in the first callout: identity and package claims only; not substitutes for OEM electrical or motion documentation.

**Documentation reviewed:** current product page, all 16 Go2-W V1.1 manual pages, all 21 actual Go2-W portal record bodies, three explicitly delegated Go2 service articles, one Go2 dock chapter with named Go2-W resources and two additional model-bounded navigation/recharge references, and pinned software sources. Draft limits remain for the delivered U-package/BOM, conflicting source performance/compute entries, exact battery and handheld instructions, connector polarity/current limits, firmware/network pairing and firmware recovery. These are narrower than the now-filled operating-manual gap.

**Software execution:** SDK installation, compilation, DDS communication and ROS were not run. Any saved syntax/static checks validate only the original example's structure.

**Hardware validation:** not run. No power, charging, motion, wheel direction, calibration, payload, firmware update or recovery was tested. No GitBook publication was performed.

**Related documentation:** [Unitree robot and development directory](./).

**Related documentation:** [Unitree model and development directory](./).
