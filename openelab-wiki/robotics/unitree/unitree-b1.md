---
description: >-
  Identify Unitree B1 whole-robot specifications and legacy SDK exclusions,
  separate simulation from hardware support, and complete an offline
  compatibility checkpoint before activation.
---

# Unitree B1: specifications and unresolved SDK compatibility

{% hint style="info" %}
**Manufacturer model reference: Unitree B1.** No exact B1 whole-robot OpenELAB listing or SKU was verified in the observed catalog. **SKU:** unverified · **Store URL:** unverified. B1-16 is a motor/component name, not a verified B1 robot package. [Official Unitree B1 page](https://www.unitree.com/b1/).
{% endhint %}

## Product overview <a href="#product-overview" id="product-overview"></a>

Unitree B1 is an earlier industrial quadruped with a published approximately 50 kg whole-machine mass, 20 kg continuous-walking payload and Intel i5-1135G7 main-control CPU. It remains linked in the observed manufacturer range; navigation presence proves neither current production nor retirement. This page supplies a B1-specific source reference and an offline compatibility checkpoint. It does not turn [B2](unitree-b2.md) or [B2-W](unitree-b2-w.md) SDK examples into B1 commissioning instructions. [B1 primary parameter table](https://www.unitree.com/b1/)

The most important development limit is unresolved SDK support. The inspected legacy SDK v3.8.6 explicitly excludes B1, and its pointer to v3.3.1 does not establish B1 support: that historical README names Aliengo and A1, not B1. No SDK2/firmware pairing, B1 power/stop manual or connector pinout was verified in this task. A source-only reference is useful; a guessed live robot procedure would not be.

## Applications <a href="#applications" id="applications"></a>

The manufacturer describes agriculture, industrial work, inspection/security patrol research, surveys and rescue/exploration applications. Its published load and endurance values support early sizing, with actual terrain and payload validation still required. A payload attached above the chassis changes balance and electrical demand; the 80 kg maximum standing number is not a continuous walking allowance.

For engineers working with an existing B1, the first useful task is reconstructing a trustworthy unit record: exact body/controller/battery revisions, approved software and available manuals. Visualizing a B1 URDF can be a separate simulation task, but model assets do not validate hardware communications or a controller image. B1 carries no B2-Ex hazardous-area certification implication. [Official B1 overview and notes](https://www.unitree.com/b1/)

## Specifications <a href="#specifications" id="specifications"></a>

| Parameter                 | Manufacturer B1 value and qualification                                                                                                                                                                       |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Standing size, L × W × H  | 1126 × 467 × 636 mm.                                                                                                                                                                                          |
| Folded size, L × W × H    | 1202 × 467 × 297 mm. Folded length being larger than standing length is what the page reports; do not swap dimensions to make them look conventional.                                                         |
| Mass                      | Whole machine including battery about 50 kg; battery about 5 kg. Delivered accessories are not separately accounted for by those rows.                                                                        |
| Payload                   | Continuous walking 20 kg; maximum standing 80 kg. The source recommends keeping carried load within 20 kg.                                                                                                    |
| Endurance                 | Standing 5 h; continuous unloaded walking 2 h. The page qualifies the values by ideal conditions and dependence on load, body height, ground flatness and ambient temperature.                                |
| Control / sensing compute | Intel i5-1135G7 main CPU. The sensing-compute row lists multiple brands/models and Xavier NX ×3; confirm the actual delivered arrangement and OS image.                                                       |
| Perception                | Intel RealSense D430 ×5 in the product table; no calibration, stream format or installed-device count was independently checked.                                                                              |
| Battery table             | Lithium; 18000 mAh; rated 51.8 V; rated energy 932.4 Wh; charge-limit voltage 58.8 V; charge-time headline 1–2 h. These are product-table figures, not a verified charger model/output-current specification. |
| Expansion table           | Standard output 12 V/24 V; Gigabit interface ×7, RS-485 ×4, USB ×5 and CAN ×4. No polarity, current budget, bus bitrate or mating pinout is supplied by these counts.                                         |
| Battery temperature row   | −5 to +45 °C. This is listed under Battery; it is not evidence of the complete robot's certified operating or charging temperature range.                                                                     |
| Stair capability          | Maximum step height 20 cm, product-table capability only; no mode/approach/traction procedure was read.                                                                                                       |
| Protection headline       | “IP68 Waterproof” is the page's headline. No report, immersion depth/time, seals/connector configuration or test conditions were verified.                                                                    |
| Other protection wording  | Temperature/current protection is listed; thresholds and stop/recovery behavior are not supplied in the table.                                                                                                |

Source: [B1 Product Parameters and accompanying endurance/load notes](https://www.unitree.com/b1/). The battery and interface rows above are actual product-page entries. No charger output current, accessory current budget, connector pinout, joint torque or travel-speed number is invented to fill the remaining gaps. Data from B1 motor products, B2 or B2-W is not substituted.

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

### Inventory without activating the robot <a href="#inventory-without-activating-the-robot" id="inventory-without-activating-the-robot"></a>

For an unpowered B1, preserve and record the body/controller/pack/charger nameplates and any commissioning record. Check whether the robot is legged B1 and whether an arm or sensor superstructure is installed. Its approximately 50 kg mass is a planning input, not a lifting method: approved lifting points, handling personnel/equipment and limb arrangements need the B1 mechanical instructions.

The [manufacturer illustration resource](https://oss-global-cdn.unitree.com/static/e218a67508be4ec0b8145e1e8e89924a_776x655.png) is an observed page image, not a mating-connector or dimensioned mounting drawing. No electrical pinout, battery insertion orientation, latch sequence, power-button timing, charger pairing or first power-on posture was established by the read product page. Keep the system unpowered during this guide's checkpoint rather than guessing from another quadruped.

### Power, environment and stop conditions remain prerequisites <a href="#power-environment-and-stop-conditions-remain-prerequisites" id="power-environment-and-stop-conditions-remain-prerequisites"></a>

The product table’s −5 to +45 °C battery row cannot establish charging temperatures or authorize use of a third-party charger. Its rated 51.8 V and charge-limit 58.8 V are different quantities, not interchangeable supply settings. The 5 kg battery weight does not establish electrical compatibility with another pack. Require an exact battery/charger manual and label match, including rated voltage, maximum charge voltage/current, connector polarity and charging-state requirements before any later charging action.

Likewise, an IP68 headline does not establish how long/deep the delivered configuration may be immersed, whether the battery can be removed wet, or whether added connectors preserve the rating. Do not perform an immersion or pressure-cleaning test from this guide. Inspect the actual sealing/cable configuration under the manufacturer procedure once obtained.

No B1 remote key mapping, independent emergency-stop design, state on communication loss or power-loss recovery behavior was read. Do not inherit B2's L2+A/L2+B actions or its automatic-standing startup. Do not assume a software API StopMove, a radio link light or Ethernet removal is a verified independent stop. The missing B1 stop/isolation and handling instructions block a live first result.

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### The legacy SDK redirect is not B1 support evidence <a href="#the-legacy-sdk-redirect-is-not-b1-support-evidence" id="the-legacy-sdk-redirect-is-not-b1-support-evidence"></a>

| Source                                                                                | What was actually read                                                                                                              | B1 conclusion                                                                                                                     |
| ------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| `unitree_legged_sdk` commit `4539a6c10dfbc9781cea6fcb7d51bc6ddc6f71e1`, README v3.8.6 | Supports Go1; explicitly lists B1 among unsupported robots, and points to v3.3.1 for other support.                                 | **This version does not support B1 according to its README.** Go1 firmware minima are not B1 requirements.                        |
| Historical `v3.3.1` README                                                            | Names Aliengo and A1 (`sport_mode >=v1.19` for A1); explicitly excludes Laikago and Go1; does not name B1.                          | The redirect does not verify B1. Absence is not converted into a support claim or a tested incompatibility claim for all history. |
| SDK2 C++ snapshot `b7fec6020eb93d4c059a6edf19905e12a75a8d3d`                          | B2/B2-W-specific examples and GO contracts were reviewed.                                                                           | No B1-specific SDK2 or firmware pairing was established.                                                                          |
| `unitree_ros` commit `157ff950351e5f535e03c5d85a16b7d594b3dbcc`                       | Robot-description table includes B1 and a 12-DoF model; Gazebo controller configuration lists B1 among supported simulation models. | Simulation/model availability is separate from an exact B1 real-hardware driver/firmware guarantee.                               |

Sources: [legacy v3.8.6 README at pinned commit](https://github.com/unitreerobotics/unitree_legged_sdk/blob/4539a6c10dfbc9781cea6fcb7d51bc6ddc6f71e1/README.md), [actual historical v3.3.1 README](https://github.com/unitreerobotics/unitree_legged_sdk/blob/v3.3.1/README.md), [ROS description/simulation scope](https://github.com/unitreerobotics/unitree_ros/blob/157ff950351e5f535e03c5d85a16b7d594b3dbcc/README.md). The historical tag was retained with a content hash; no resolved immutable commit for that tag is asserted here.

The legacy README's UDP transport, dependencies and firmware values belong to its declared models. The newer SDK2 CycloneDDS ecosystem is a different contract. Do not initialize a guessed B1 DDS participant, use GO motor offsets because B1 also has twelve joints, or run B2/Go1 examples against a B1 controller. A standalone B1-motor driver concerns rotor/motor interfaces, not whole-robot control support.

For later development, obtain a manufacturer-confirmed B1 SDK release and license, exact robot/controller/image target, supported OS/toolchain, protocol/message definitions, endpoint/interface plan, sample timing and an approved receive-only diagnostic. The [shared SDK2 guide](unitree-sdk2-state-development.md) and [ROS 2 guide](unitree-ros2-integration.md) can explain their own ecosystems, but do not close the B1 compatibility gap. No installation/build command is proposed here.

## Getting started <a href="#getting-started" id="getting-started"></a>

### Offline first result: make the compatibility decision explicit <a href="#offline-first-result-make-the-compatibility-decision-explicit" id="offline-first-result-make-the-compatibility-decision-explicit"></a>

1. Keep the B1 and network unchanged. Assemble its model/revision/nameplate record and locate the exact approved SDK/firmware documentation; record missing items honestly.
2. Read the two legacy support statements above. Mark v3.8.6 as explicitly unsupported for B1, and v3.3.1 as not verified for B1, rather than treating the redirect as a successful match.
3. Run this original Python 3 evidence worksheet locally. It uses only synthetic, source-derived decision labels and starts no vendor code or network activity.

```python
support = {
    "model": "B1",
    "legacy_3_8_6": "explicitly unsupported in README",
    "legacy_3_3_1": "B1 not named; not verified",
    "sdk2_firmware_pair": None,
    "b1_power_and_stop_manual": None,
}
required = ("sdk2_firmware_pair", "b1_power_and_stop_manual")
missing = [name for name in required if not support[name]]
assert missing == ["sdk2_firmware_pair", "b1_power_and_stop_manual"]
print({"model": support["model"], "evidence_inventory_complete": not missing,
       "hardware_support_verified": False,
       "missing_evidence": missing, "data_origin": "offline worksheet"})
```

**Expected result:** `model: B1`, `hardware_support_verified: False` and both missing-evidence keys. This correctly bounded result is not a live telemetry sample or proof that SDK2 could never support any B1 revision. It states that this evidence set cannot justify activation.

A later first hardware result should be a manufacturer-supported, bounded read of identity/status from the confirmed B1 release, with source identity, units, freshness, interface and recovery/stop conditions documented first. Do not replace that missing receive-only example with a motor torque test, stand demo, calibration or firmware flash. No live run is authorized or performed by this reference workflow.

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

**The current SDK README directs me to v3.3.1. Is that sufficient?** No. Read the destination: it names Aliengo/A1, not B1. Obtain an exact B1 support statement and firmware pairing instead of guessing a historical binary.

**Can a B1 Gazebo model prove real-robot support?** No. URDF/joint-controller descriptions establish simulation scope. Real communication requires a matching hardware protocol, network endpoint, controller/image and stop behavior; a twelve-joint model is insufficient evidence.

**Does “B1 motor” support imply the B1 robot is supported?** No. A motor's electrical/serial and rotor-scaling API is a different scope from the robot controller and joint-level safety system. Never transplant motor raw units into a whole-body command.

**Can I use the 80 kg payload for walking?** The table separately lists continuous walking 20 kg and recommends keeping carried load within 20 kg. Standing maximum, mounting moments and dynamic stability are separate conditions.

**Can I use B2's charger or remote instructions?** No explicit B1 compatibility was verified. Match the delivered B1 pack, charger and remote manual before power, charging or command actions.

**Is B1 discontinued?** The observed manufacturer navigation still links B1, but that alone proves neither manufacturing availability nor retirement. No stock, shipment or lifecycle claim is made here.

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

| Resource                                                                                                                               | Purpose and evidence boundary                                                                                         |
| -------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| [Official B1 product page](https://www.unitree.com/b1/)                                                                                | Whole-robot identity, dimensions, mass, load/endurance conditions, CPU and battery-temperature row.                   |
| [Legacy current README](https://github.com/unitreerobotics/unitree_legged_sdk/blob/4539a6c10dfbc9781cea6fcb7d51bc6ddc6f71e1/README.md) | Read the explicit B1 exclusion; not an install recipe for B1.                                                         |
| [Historical v3.3.1 README](https://github.com/unitreerobotics/unitree_legged_sdk/blob/v3.3.1/README.md)                                | Read actual supported models; no B1 support inferred from a redirect.                                                 |
| [ROS model catalog](https://github.com/unitreerobotics/unitree_ros/blob/157ff950351e5f535e03c5d85a16b7d594b3dbcc/README.md)            | B1 description/simulation discovery, not live hardware validation.                                                    |
| Exact B1 user/remote/battery/charger, wiring/mechanical, calibration and recovery manuals                                              | Not established in the English manual collection reviewed for this task. Do not replace with B2/B2-W chapters.        |
| Exact B1 SDK release/firmware or independent IP68 report                                                                               | Not read/verified. Required before the corresponding hardware or environmental claim can become operational guidance. |

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

Reviewed 24 November 2026 from the official B1 product content, the two actual legacy README texts, the SDK matrix and the scoped ROS model description. Source content hashes and the historical tag reference are retained privately. No complete B1 manual or support-portal chapter set was read; newly accessible parent browser articles remain separate evidence until actually reviewed.

**Validation:** original offline worksheet, source/hash/structure and unsupported-transfer checks only. **Not performed:** vendor import/execution, SDK installation/build, ROS/DDS/network discovery, hardware, motion, charging, calibration or firmware flashing. Hardware readiness remains draft because exact power, stop and SDK/controller/firmware support are unresolved.

**Related documentation:** [Unitree model and development directory](./).
