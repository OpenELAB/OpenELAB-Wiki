---
description: >-
  Compare Dex5-S and Pro power, 22-axis actuation and interface options while
  identifying the exact wiring, protocol and tactile evidence needed before
  connection.
---

# Unitree Dex5-S and Pro: 22-axis hand integration boundaries

{% hint style="info" %}
**Model reference — unlisted store product.** This guide covers the manufacturer's Dex5-S and Dex5-S Pro comparison, as one product family reference. No OpenELAB SKU or product URL was verified for either edition. Pro adds listed tactile sensing; it does not establish a Dex5-1P-compatible sensor layout. Hardware readiness is **draft** pending the delivered interface, wiring, firmware and stop contract. [Manufacturer comparison](https://www.unitree.com/Dex5-S).
{% endhint %}

## Product overview <a href="#product-overview" id="product-overview"></a>

Dex5-S is a five-finger hand with22 described degrees of freedom and22 motors: five for the thumb, four each for index, middle and ring, and five for the pinky. The additional pinky roll axis and fully actuated layout distinguish it from Dex5-1's20 joint slots associated with16 motors and from the two-actuator Dex2/5. Neither hand's joint sequence, transmission ratios or command array can be transferred here. [Actuation and parameter table](https://www.unitree.com/Dex5-S).

The manufacturer describes backdrivability, dual encoders, impact protection on all22 axes and precision micro gearboxes. Its marketing also uses “direct-drive”; together these statements do not establish a gearbox-free motor-to-joint relation. Impact protection is a mechanical claim, not an independent emergency stop or a collision-force limit. [Actuation, protection and precision](https://www.unitree.com/Dex5-S).

The source distinguishes the base and Pro primarily through tactile sensing: base is marked “/”, Pro “YES”. Their listed dimensions, mass, supply, power and axis counts match. There is no verified tactile taxel count, calibration, message schema, hand-side convention or firmware matrix in that comparison. Price is intentionally omitted because the captured starting price does not define an edition, shipping scope or current quotation.

## Applications <a href="#applications" id="applications"></a>

The22 axes make the hand relevant to articulated manipulation research, grasp shape studies and data collection where independent finger placement matters. A useful initial engineering task is to reconcile a delivered assembly's axis list and interface option against its manufacturer documentation while the hand remains unpowered. The extra pinky axis must be included in any model; assigning a20-slot Dex5-1 motion vector would lose or misidentify axes. [Degrees of freedom](https://www.unitree.com/Dex5-S).

The1 kg continuous and2 kg peak per-hand payload claims are distinct operating conditions. A short demonstration at2 kg cannot establish continuous carrying performance, allowable acceleration or thermal margin. Select fixtures and retention separately for the actual object, orientation and task; the page supplies no approved payload curve or sustained duty cycle beyond the continuous headline. [Power and payload table](https://www.unitree.com/Dex5-S).

Pro may support tactile observations after its delivered sensor map, scaling, calibration and timing are established. “Tactile sensing: YES” does not justify a force-controlled grasp or a Newton-valued output. A camera connection through the Gigabit Ethernet configuration also does not establish camera inclusion, an image API, synchronized timestamps or optical calibration. [Interfaces and sensing comparison](https://www.unitree.com/Dex5-S).

The source includes As2 single-arm and A2 dual-arm movement footnotes. Those refer to robotic-arm/body constraints; they are not a qualified Dex5-S wrist-mounting, electrical or firmware compatibility matrix. Obtain the exact host adapter and harness documentation rather than inferring compatibility from surrounding website text.

## Specifications <a href="#specifications" id="specifications"></a>

| Item                      | Dex5-S                                    | Dex5-S Pro | Engineering interpretation                                  |
| ------------------------- | ----------------------------------------- | ---------- | ----------------------------------------------------------- |
| Actuated/described axes   | 22/22                                     | 22/22      | Thumb5; index/middle/ring4 each; pinky5; no verified order  |
| Dimensions L×W×H          | 102×187×26 mm                             | Same       | Product dimensions; not a flange drilling drawing           |
| Mass                      | 620 g                                     | Same       | Include cable, camera and adapter separately                |
| Housing / encoders        | Aluminum alloy / dual                     | Same       | No published encoder bit depth or calibration here          |
| Continuous / peak payload | 1 kg /2 kg                                | Same       | Per hand; peak duration and orientation not specified       |
| Supply / power connector  | 15–65 V / XT30                            | Same       | Connector name alone does not identify cavity polarity      |
| Peak power                | 200 W                                     | Same       | No continuous input rating or start-current budget verified |
| Ethernet option           | 1000BASE-T1 configuration                 | Same       | See terminology conflict below; no RJ45/PoE assumption      |
| Protocol row              | T1s Ethernet×2; high-speed RS485×1; USB×1 | Same       | Verify delivered option and physical layer                  |
| Serial headline           | 6 Mbps                                    | Same       | Bit rate is not the control-loop rate                       |
| Listed control loop       | Ethernet/USB1000 Hz; RS48550 Hz           | Same       | No measured application latency guarantee                   |
| Tactile sensing           | “/”                                       | “YES”      | Pro count, units and calibration unverified                 |

All table values come from the [manufacturer's exact comparison](https://www.unitree.com/Dex5-S). It lists feedback as joint mode, position, velocity, torque, temperature, voltage and current; command concepts are joint mode, position, velocity, torque, stiffness and damping. These are named quantities, not a serialized protocol definition. Units, limits, signs and frame orientation still need the matching integration document.

The Ethernet rows use both “1000BASE-T1” and “T1s”. Preserve that ambiguity: do not substitute a conventional PC Ethernet lead, a T1S transceiver, a PoE injector or an assumed switch topology. The page does not verify an IP address, transport protocol, DDS domain or network discovery behavior. No operating-temperature range, IP rating, chemical resistance or hazardous-area certification was verified for this model. Dex5-1's temperature range cannot fill those gaps.

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

### Power and mechanical interface <a href="#power-and-mechanical-interface" id="power-and-mechanical-interface"></a>

Keep the hand unpowered until the exact delivered XT30 polarity, connector view, mating part and harness are documented. The15–65 V range and200 W peak do not supply a complete fuse/current-limit/inrush specification. Do not choose cable gauge or a current limit by dividing200 W by an arbitrary supply voltage alone. Separate approved power, communication, shielding and return paths from host mechanical support. [Electrical characteristics](https://www.unitree.com/Dex5-S).

The102×187×26 mm envelope is not a mounting template. Obtain the flange drawing, fastener diameter, engagement depth, torque, cable exit and strain relief for the exact side and revision. Keep fingers clear of fixtures while documenting axis ranges. Backdrivability does not establish that manually forcing a joint beyond an unknown travel limit is safe. No calibrated angular limits were available in the comparison.

### Communication variants and camera <a href="#communication-variants-and-camera" id="communication-variants-and-camera"></a>

Identify the delivered interface option before connecting anything. The manufacturer offers Ethernet, USB and high-speed RS485, but the table's aggregate interface counts do not prove every delivered configuration exposes all ports simultaneously. No cavity pinout, bus termination, USB power role, RS485 address or camera connector was verified. A USB connector must not be treated as the motor supply, and the XT30 label must not be interpreted using another hand's photographed wiring. [Three interface options](https://www.unitree.com/Dex5-S).

The stated camera passthrough is limited to the Gigabit Ethernet configuration. Confirm camera model, supply, bandwidth, connector, driver and synchronization as separate dependencies. No camera appears in the base/Pro comparison as a verified included accessory. Avoid importing Dex1-1's RGB/D405 bundle contents into this product.

### Stops and restart conditions <a href="#stops-and-restart-conditions" id="stops-and-restart-conditions"></a>

Before any later powered work, require an approved independent stop, behavior on lost communication, torque-off versus holding behavior, restart/reset semantics and a safe object-release plan. Commands containing zero torque or zero gains may still change holding behavior; no Dex5-S source here proves their stop semantics. The impact-protection feature is not evidence of a safety-rated control function. This guide therefore provides an offline first result only.

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### Model contract before SDK selection <a href="#model-contract-before-sdk-selection" id="model-contract-before-sdk-selection"></a>

The available primary evidence is the exact product comparison. A search across the628-record saved portal corpus did not locate a dedicated Dex5-S protocol article; that is a search result, not a claim to have semantically reviewed every article. No matching SDK release, supported OS, firmware range, command frame/CRC, axis ordering, control-mode values or public URDF was verified. Obtain a revision-matched manufacturer's integration package before selecting a driver. [Product source](https://www.unitree.com/Dex5-S).

The public SDK2 repository at commit `b7fec6020eb93d4c059a6edf19905e12a75a8d3d` contains HG HandCmd/HandState declarations used by other hand material. Its existence does **not** establish a Dex5-S binding. In particular, Dex5-1's20-slot mapping,16 motors,94 tactile sensors and mixed torque-unit discussion do not become Dex5-S definitions. The22-axis product table gives a count, not a field layout. [Pinned SDK inventory](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/README.md), [HG HandCmd declaration](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/hg/HandCmd_.hpp).

If a later confirmed bridge uses that SDK pin, match its real headers. `ChannelFactory::Init` at this commit accepts domain and interface, without the portal's additional shared-memory argument. A subscriber receives; it is not evidence of a send-channel operation. Neither a domain ID nor selecting a network adapter is an isolation or authorization mechanism. No SDK recipe or network activation is required for the offline result below. [Pinned factory](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/channel/channel_factory.hpp), [pinned subscriber](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/channel/channel_subscriber.hpp).

### Ownership and timing <a href="#ownership-and-timing" id="ownership-and-timing"></a>

A future driver must define which layer owns mode, calibration, joint limits, watchdog, transport and stop state. If data arrive asynchronously, copy fields into immutable application-owned snapshots and preserve device timestamps/counters, local monotonic receipt time and loss indicators separately. A fresh local callback alone cannot prove the actuator produced new data. The advertised1000/50 Hz interface-specific loops do not establish device timestamps, DDS rates, control deadlines or torque-loop determinism. [Feedback and rate rows](https://www.unitree.com/Dex5-S).

## Getting started <a href="#getting-started" id="getting-started"></a>

1. Keep the robot and hand unpowered; use an ordinary offline workstation.
2. Copy only the original Python program below into the named local file.
3. Run it with Python 3 and compare the **Expected output**; an offline pass does not authorize hardware.

### First result: document completeness without connecting a hand <a href="#first-result-document-completeness-without-connecting-a-hand" id="first-result-document-completeness-without-connecting-a-hand"></a>

Create a local `dex5s_gate.py` file containing the original program below. It uses only Python's standard library and synthetic paperwork status. It imports no SDK, opens no port and never authorizes hardware. Run `python3 dex5s_gate.py` on an ordinary offline workstation.

```python
from dataclasses import dataclass

REQUIRED = ("harness_pinout", "interface_option", "firmware_protocol",
            "axis_order_units", "stop_restart_behavior")

@dataclass(frozen=True)
class Report:
    model: str
    axes: int
    missing: tuple[str, ...]
    hardware_authorized: bool = False

def review(model, evidence):
    if model not in ("Dex5-S", "Dex5-S Pro"):
        raise ValueError("exact Dex5-S edition required")
    if not isinstance(evidence, dict):
        raise ValueError("evidence must be a dictionary")
    if any(type(value) is not bool for value in evidence.values()):
        raise ValueError("use explicit boolean document-review markers")
    missing = tuple(key for key in REQUIRED if evidence.get(key) is not True)
    return Report(model, 22, missing)

if __name__ == "__main__":
    report = review("Dex5-S Pro", {})
    print(f"OFFLINE BLOCKED: {report.model}; axes={report.axes}; "
          f"missing={len(report.missing)}")
    print(f"hardware_authorized={report.hardware_authorized}; "
          "tactile_force_N=unverified")
```

Expected output:

```
OFFLINE BLOCKED: Dex5-S Pro; axes=22; missing=5
hardware_authorized=False; tactile_force_N=unverified
```

This result means the missing integration contracts have been identified. Markers are review bookkeeping, not authenticated certificates; even marking all five true leaves `hardware_authorized=False`. Use actual matching documents to review each item, retain their revision and have the responsible integrator independently qualify hardware work. A successful script run establishes only the behavior of this original offline worksheet.

### Later powered-work gate <a href="#later-powered-work-gate" id="later-powered-work-gate"></a>

Before proceeding beyond this guide, reconcile model/side/edition, interface option, host adapter and mounting drawing; approve the supply/harness and all connector views; obtain exact protocol frames, axis order/sign/units and firmware support; establish a verified stop/loss/restart procedure; and validate tactile calibration separately if Pro is fitted. No motion publisher, vendor server, firmware utility or configuration change is the first check here. Missing electrical or stop evidence remains a blocker even when an SDK example compiles.

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

### Can the Dex5-1 example be reused because the name is similar? <a href="#can-the-dex5-1-example-be-reused-because-the-name-is-similar" id="can-the-dex5-1-example-be-reused-because-the-name-is-similar"></a>

No supported binding was established. Dex5-S has22 motors; Dex5-1 documentation describes20 joint slots mapped to16 motors. An array length change alone cannot reconcile ordering, transmission, gains, firmware or packet format. Obtain the exact manufacturer driver and schema before writing an adapter. [Dex5-S axes](https://www.unitree.com/Dex5-S), [comparison schema listing](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/hg/HandCmd_.hpp).

### Why does a6 Mbps serial interface list only50 Hz control? <a href="#why-does-a6-mbps-serial-interface-list-only50-hz-control" id="why-does-a6-mbps-serial-interface-list-only50-hz-control"></a>

They describe different layers. The product assigns50 Hz to high-speed RS485 and1000 Hz to Ethernet/USB, while separately listing6 Mbps. Packet overhead, scheduling and implementation details were not verified. Do not promise a1000 Hz RS485 application loop from its bit-rate headline. [Communication rows](https://www.unitree.com/Dex5-S).

### Does Pro provide94 force values or calibrated Newton readings? <a href="#does-pro-provide94-force-values-or-calibrated-newton-readings" id="does-pro-provide94-force-values-or-calibrated-newton-readings"></a>

The comparison only confirms tactile sensing presence. It does not give94, a pressure array length, a channel order or a calibration equation. Preserve unknowns and request the Pro-specific tactile definition. Raw pressure, temperature, torque estimates and actual object-contact force are distinct quantities.

### Can I choose an Ethernet cable from the label? <a href="#can-i-choose-an-ethernet-cable-from-the-label" id="can-i-choose-an-ethernet-cable-from-the-label"></a>

The “1000BASE-T1” versus “T1s” wording needs clarification along with connector and transceiver type. Do not assume RJ45 or PoE. Confirm the delivered physical layer and approved wiring with the manufacturer before connection. [Electrical table](https://www.unitree.com/Dex5-S).

### Is2 kg continuous duty or is impact protection a stop? <a href="#is2-kg-continuous-duty-or-is-impact-protection-a-stop" id="is2-kg-continuous-duty-or-is-impact-protection-a-stop"></a>

The comparison says1 kg continuous and2 kg peak. It does not specify a duration for the peak or a safety-rated stop. Mechanical impact protection and dual encoders do not establish allowable collision energy or a certified emergency stop. Use the exact payload/duty and stop specification for the intended installation.

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

| Resource                                                                                                                                                                                                                                                                                                                             | Access and use                                                                      |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------- |
| [Dex5-S / Pro manufacturer comparison](https://www.unitree.com/Dex5-S)                                                                                                                                                                                                                                                               | Actual saved HTML and text read; all functional/electrical table rows covered above |
| [Pinned SDK2 README](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/README.md)                                                                                                                                                                                                        | Common repository inventory only; not verified Dex5-S support                       |
| [Pinned HG HandCmd declaration](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/hg/HandCmd_.hpp)                                                                                                                                                                   | Used to explain why another hand's schema is insufficient; not a Dex5-S protocol    |
| [Pinned factory](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/channel/channel_factory.hpp) · [subscriber](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/channel/channel_subscriber.hpp) | Static API boundary; no executable integration recipe                               |
| Exact flange/pinout/harness drawings                                                                                                                                                                                                                                                                                                 | Not verified in the read source; request matching side/revision                     |
| Dex5-S firmware/driver, protocol and OS matrix                                                                                                                                                                                                                                                                                       | Not verified; required before powered integration                                   |
| Pro tactile layout, calibration and camera API                                                                                                                                                                                                                                                                                       | Not verified; do not substitute Dex5-1P or Dex1 resources                           |

There is no verified model-specific CAD, calibration file, binary package or full user manual to download from the read product page. Website navigation or a similarly named hand is not a substitute. No local source cache is offered as a manufacturer-approved redistributable package.

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

Reviewed24 November2026 against the captured manufacturer comparison and pinned common SDK declarations. The628-record portal cache was searched for this model; only model-relevant actual sources read are claimed as coverage. Unrelated arm footnotes were explicitly excluded. No store identity, compatibility matrix, firmware range or electrical pinout was invented.

The original offline worksheet was checked with synthetic missing/complete evidence, wrong-model and wrong-type cases. No vendor code, SDK import, install/build, ROS/DDS, USB/network/hardware, motion, calibration or firmware operation was performed. Hardware readiness remains **draft**. Parent integration may bind related canonical hand/host guides later without changing this reference's unlisted identity.

**Related documentation:** [Unitree model and development directory](./).
