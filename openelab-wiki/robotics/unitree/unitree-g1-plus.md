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

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

### External runtime power is not a verified pinout <a href="#external-runtime-power-is-not-a-verified-pinout" id="external-runtime-power-is-not-a-verified-pinout"></a>

G1+ advertises continuous external power/charging, and its original figure identifies a rear external input at DC 54.6 V, ≤7.4 A. The specification table separately lists a 54 V / 5 A charger. These labels do not establish the same adapter, mating connector, polarity, current-limiting behavior, grounding, insertion sequence, permissible simultaneous battery state or a firmware interlock. **Do not connect a bench supply or reuse base-G1 charging instructions.** Obtain the exact G1+ user and battery/power manual, approved adapter part number/nameplate and wiring before energizing either interface. [G1+ official page and feature figure](https://www.unitree.com/G1pl/)

A 13-series pack count is not a published safe nominal voltage or user-accessible GPIO level. No verified peripheral output budget, connector orientation, CAN/serial bus map, user Ethernet port/subnet, mounting torque or protective-stand rating was read for G1+. Port and charging work remains blocked. The folded dimensions describe an envelope; they do not authorize physically folding powered joints or using a G1 packing posture.

### Match the option set mechanically and logically <a href="#match-the-option-set-mechanically-and-logically" id="match-the-option-set-mechanically-and-logically"></a>

G1+ base body arithmetic is 12 leg + 10 arm + 1 waist + 2 head = **25 axes**. An EDU configuration can add waist, wrist and hand axes. The manufacturer's 25–45 range therefore cannot be converted into one default “45-joint G1+ EDU.” Retain the purchased option list, joint names, active axes, hand model, sensor/compute options and their documentation as one configuration record. This arithmetic is engineering interpretation of the published rows, not a delivered motor-ID map. [G1+ DoF table](https://www.unitree.com/G1pl/)

No G1+-specific startup posture, battery installation sequence, remote pairing or stop/recovery procedure was observed in the exact-model documentation reviewed here. The base G1 manuals and H2 emergency-stop manual are **not established as applicable**. Keep G1+ disconnected for this guide's first result. Before later power, obtain exact G1+ commissioning/stop instructions and match them to the delivered firmware and controller revision; do not assume a remote button provides a braking hold in custom low-level mode.

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### What is actually supported by the reviewed evidence <a href="#what-is-actually-supported-by-the-reviewed-evidence" id="what-is-actually-supported-by-the-reviewed-evidence"></a>

The pinned `unitree_ros` README explicitly lists G1+ as `robots/g1_description/g1_pl.urdf`, with **31 actuated joints** in its model table. It explains that G1+ is a URDF variant inside `g1_description`. The product table, by comparison, spans 25–45 depending on edition and options. These statements describe different scopes: a specific model asset and a product range. Neither proves that the purchased unit has 31 active motors. [Pinned model catalog, commit `157ff950351e5f535e03c5d85a16b7d594b3dbcc`](https://github.com/unitreerobotics/unitree_ros/blob/157ff950351e5f535e03c5d85a16b7d594b3dbcc/README.md)

The exact URDF was listed in that read README, but its raw download timed out during this guide's research. Its joints, limits, transforms, mesh dependencies and license scope were therefore **not independently inspected**. Do not claim a working G1+ simulator from the catalog row. The README limits its complete Gazebo controller setups to specific quadrupeds and says other descriptions ship display/RViz files only; it does not establish a G1+ locomotion controller.

| Resource / claim                        | Observed state                                                                                  | Correct use                                                       |
| --------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| G1+ developer entitlement               | Product EDU column says Yes; base slash                                                         | Identify edition, then obtain exact development documentation     |
| G1+ description asset                   | `g1_pl.urdf` listed in read official model catalog; raw body not read                           | Candidate kinematic reference requiring file/configuration review |
| C++ SDK2                                | Commit `b7fec6020eb93d4c059a6edf19905e12a75a8d3d`; file tree has no explicitly named G1+ target | No exact G1+ hardware support asserted                            |
| Python SDK2                             | Commit `814556d15970dd2ecf1c9984e845ca02ab07e206`; file tree has no explicitly named G1+ target | G1 examples do not become G1+ examples                            |
| G1/G1 EDU examples                      | Related-model software exists                                                                   | No G1+ IDL, joint count, mode or API compatibility inferred       |
| Firmware/image, transport, OS/toolchain | No exact G1+ compatibility matrix read                                                          | Install/build, ROS/DDS and connected tests remain deferred        |

The absence of a named path in those pinned trees is a bounded finding, not proof that Unitree never supports G1+. A developer manual, release note or exact target example could resolve it. The required answer must name model, edition, SDK commit/package, firmware range, topic/schema, active joint map and stop/ownership behavior together. No such complete pairing was verified here.

## Getting started <a href="#getting-started" id="getting-started"></a>

### Prerequisites and model qualification <a href="#prerequisites-and-model-qualification" id="prerequisites-and-model-qualification"></a>

Keep G1+ disconnected. Use a browser for source inspection and, optionally, Python 3 for the standalone synthetic example. No exact G1+ live API/firmware pairing is established here. Base G1 software must not be substituted for that missing contract.

### First working result: distinguish a model asset from a hardware target <a href="#first-working-result-distinguish-a-model-asset-from-a-hardware-target" id="first-working-result-distinguish-a-model-asset-from-a-hardware-target"></a>

1. Open the [official G1+ product table](https://www.unitree.com/G1pl/). Record G1+ base 25 DoF versus G1+ EDU 25–45 DoF, and the separate secondary-development entries. Keep the `+` in the identity.
2. Open the [official model catalog at commit 157ff950](https://github.com/unitreerobotics/unitree_ros/blob/157ff950351e5f535e03c5d85a16b7d594b3dbcc/README.md). Find the G1+ row, `g1_pl.urdf`, its 31-joint model scope and the explanation that it is a variant inside `g1_description`. A catalog listing is not an inspection of the URDF's internal joints.
3. Inspect the [C++ SDK2 tree at commit b7fec602](https://github.com/unitreerobotics/unitree_sdk2/tree/b7fec6020eb93d4c059a6edf19905e12a75a8d3d) and [Python SDK2 tree at commit 814556d1](https://github.com/unitreerobotics/unitree_sdk2_python/tree/814556d15970dd2ecf1c9984e845ca02ab07e206). Look for an explicitly documented G1+ target and firmware contract. G1 examples alone are insufficient; a missing named path does not prove global non-support.
4. Record the product's option range, the specific model-catalog variant and the unresolved physical SDK/firmware mapping as three separate findings. Do not choose a 29- or 31-joint executable merely to fit a count.

**Expected result:** a note stating “G1+ base 25; EDU 25–45; catalog model 31; no exact physical API/firmware pairing established by these sources.” The result is an explicit compatibility boundary, not an approved live target. Unavailable links leave that source check incomplete.

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

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

**A search finds G1 but not G1+. Is that sufficient?** No. Preserve the manufacturer `G1pl` identity and exact model/option scope. Base G1 store products and wiki pages are related references, not G1+ matches. This guide intentionally has null SKU/store URL until an exact listing is observed. [G1+ official page](https://www.unitree.com/G1pl/)

**The URDF catalog says 31 while the product says 25–45.** Treat 31 as one named description variant, not a correction to the product table or proof of your robot's axis count. Read the actual URDF and purchased BOM, identify fixed/active/transmission joints, and obtain the controller ID map. File contents were not verified here because the raw fetch timed out. [Pinned model catalog](https://github.com/unitreerobotics/unitree_ros/blob/157ff950351e5f535e03c5d85a16b7d594b3dbcc/README.md)

**Can I calculate absolute G1+ torque from the percentage upgrades?** No absolute rating or full test basis was supplied in the read upgrade panel. Keep the relative claim with its conditions; obtain exact actuator/body limits for planning. Never use the resulting arithmetic as a command bound. [Motor-upgrade panel](https://www.unitree.com/G1pl/)

**The rear input says 54.6 V but the charger table says 54 V. Which supply is correct?** They are different source labels for different interface roles. The reviewed evidence does not establish adapter interchangeability or pinout. Ask for exact approved G1+ power parts and instructions before connecting anything. [Original feature figure](https://www.unitree.com/images/32be40654390458795e906bb649c532c_2000x1346.png?x-oss-process=image/format,webp)

**Does tapping the head only record a sensor value?** The manufacturer feature says tapping can initiate dialogue and trigger motion. Do not probe tactile behavior on a powered, unqualified unit as a passive sensor test. Obtain the touch-event API and interaction-mode behavior first. [G1+ tactile panel](https://www.unitree.com/G1pl/)

**Can I use base G1 maintenance, calibration or emergency-stop instructions?** No applicability was verified. Obtain exact G1+ manuals, controller revision and firmware-specific recovery instructions. No maintenance disassembly, calibration or reset steps are invented in this guide.

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

| Resource                  | Model / purpose                                                                        | Link                                                                                                                                                              |
| ------------------------- | -------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| G1+ product page          | Exact G1+/G1+ EDU feature and specification table                                      | [Official G1+](https://www.unitree.com/G1pl/)                                                                                                                     |
| G1+ feature diagram       | Original manufacturer illustration; touch, vision, head axes and rear power annotation | [Original figure](https://www.unitree.com/images/32be40654390458795e906bb649c532c_2000x1346.png?x-oss-process=image/format,webp)                                  |
| Official model catalog    | Pinned README with explicit G1+ description reference; read                            | [Unitree ROS model table](https://github.com/unitreerobotics/unitree_ros/blob/157ff950351e5f535e03c5d85a16b7d594b3dbcc/README.md)                                 |
| Candidate G1+ URDF        | Catalog-linked exact path; raw content unread after timeout                            | [g1\_pl.urdf at the pinned commit](https://github.com/unitreerobotics/unitree_ros/blob/157ff950351e5f535e03c5d85a16b7d594b3dbcc/robots/g1_description/g1_pl.urdf) |
| Developer document center | Obtain exact G1+ manual and firmware/SDK confirmation                                  | [Official support portal](https://support.unitree.com/main/en)                                                                                                    |

A G1+ user, battery/charger, remote and developer manual set, full schematic/pinout, delivered-unit mechanical drawing, API/firmware compatibility matrix and qualified first-state program were not observed in the reviewed sources. No manual chapter coverage is claimed for those missing documents. The existing G1 English manuals do not fill those rows. See the separate [H2](https://www.unitree.com/H2/) and [H2-X](https://www.unitree.com/H2-X/) manufacturer specifications for other models; their hardware guidance does not apply here.

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

Reviewed November 24, 2026: G1+ product text and its selected original figure; pinned `unitree_ros` README; the pinned C++/Python SDK2 file trees. The actual G1+ URDF remained unread following a direct raw-download timeout. No G1+ developer article content is claimed reviewed here.

**Readiness:** source-bounded manufacturer-reference draft. Exact store/SKU, manuals/power/stop, active hardware mapping, SDK target, firmware pairing and first live state contract remain unresolved. The source-inspection procedure and generic synthetic log check are the first results supplied.

**Vendor software execution:** not run; no SDK install/build/import, ROS or DDS. **Hardware validation:** not run; no power, tactile interaction, motion, charging, calibration or flashing. The standalone seven-case synthetic example was executed successfully; no physical compatibility is established by that result.

**Related documentation:** [Unitree model and development directory](./).
