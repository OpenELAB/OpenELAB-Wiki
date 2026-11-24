---
description: >-
  Identify the A2 autonomous charging dock, distinguish the flat contact pad and
  compute hub, and check electrical, battery and control prerequisites before
  commissioning.
---

# Unitree BA2 / A2 Autonomous Charging Dock: ratings and integration boundaries

{% hint style="info" %}
**Manufacturer reference —** [**Unitree A2 Intelligent Autonomous Charging Dock**](https://www.unitree.com/A2/ChargingDock/). This guide uses **BA2** as the requested catalog-family key for that exact dock. **No exact OpenELAB product/SKU match was observed in the complete supplied catalog; SKU and store URL remain unlisted (`null`).** No substitute battery, charger, flat pad or robot SKU is assigned.
{% endhint %}

## Product overview <a href="#product-overview" id="product-overview"></a>

The A2 Intelligent Autonomous Charging Dock is a 9.6 kg, contact-based dock intended specifically for the **Unitree A2 quadruped**. Unitree describes low-battery return, positioning, posture adjustment, docking and automatic charging, with concealed charging contacts and several electrical protection mechanisms. This is the manufacturer's integrated-dock claim; it does not establish the delivered robot's autonomous-navigation software, compatible firmware, supported batteries or a public charging-control API. [Exact official dock page](https://www.unitree.com/A2/ChargingDock/).

This product must be distinguished from the **flat A2 contact charging pad** in the developer portal and from the A2's robot-mounted **expansion/compute docking hub**. All three appear in A2 resources but have different hardware and purposes. A shared robot family or a 58.8 V output is not compatibility proof. This guide retains their differences rather than transferring procedures.

![Unitree A2 autonomous dock positioning illustration](https://www.unitree.com/images/979c7ec41ec943abb2a6b2aea76a1817_1282x707.png)

_Original manufacturer illustration from the exact dock page. It shows a positioning concept; it does not specify marker geometry, recognition protocol or verified stopping distance._

## Applications <a href="#applications" id="applications"></a>

The manufacturer positions the dock for extended unattended A2 inspection, security and industrial operation. Automatic low-battery return can reduce manual replenishment when the robot, navigation stack, dock localization and battery interface are supplied and commissioned as a compatible system. Availability depends on successful return routes, accessible docking space, localization, contact engagement, charging acceptance and fault handling; a battery-low threshold alone is not an autonomous-return implementation.

Reflective posts, QR-code markers and LiDAR-based positioning are described as possible aids. They are optional configurations rather than proof that every dock includes all markers or that a particular camera/LiDAR supports a published detector. The advertised approximately 40 mm X/Y alignment tolerance is a final engagement allowance under the manufacturer's conditions, not a path-planner goal radius, a collision clearance, or a yaw/pitch/roll tolerance.

## Specifications <a href="#specifications" id="specifications"></a>

| Parameter               | Exact autonomous dock page                                                                                       |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------- |
| Intended model          | A2; no B2/As2/Go2/humanoid compatibility established                                                             |
| Dimensions / mass       | 355 × 313 × 212 mm; 9.6 kg                                                                                       |
| Material                | PA6-GF30                                                                                                         |
| Ingress claim           | IP56 dock assembly; does not extend automatically to site mains, robot, unplugged connectors or all cable joints |
| Docking interface       | Contact-based metal contacts, concealed until the docking process                                                |
| Alignment               | Approximately 40 mm offset on X and Y; no verified rotational allowance                                          |
| AC input                | 100–240 V; maximum 5 A                                                                                           |
| No-load power           | <2 W                                                                                                             |
| DC output               | 58.8 V ±0.3 V; maximum 7.4 A; ≤437 W                                                                             |
| Full-charge termination | Voltage threshold; numeric threshold/hysteresis not disclosed                                                    |
| Operating ambient       | 0–40 °C                                                                                                          |
| Storage                 | −40 to +75 °C; not a battery storage specification                                                               |
| Protections claimed     | Overtemperature, overcurrent, short circuit, foreign-object detection, anti-arcing                               |

[Manufacturer specification table](https://www.unitree.com/A2/ChargingDock/). Values are manufacturer claims subject to actual application/product revision. The 5 A AC rating is not a 5 A DC charging-current limit; 437 W is a maximum output rating, not guaranteed continuous charging power for every battery state. The source does not provide an output current profile, charging duration, precise low-battery return threshold, efficiency, standby wake timing, cable length or grounding conductor specification.

### Related charging-pad source is different hardware <a href="#related-charging-pad-source-is-different-hardware" id="related-charging-pad-source-is-different-hardware"></a>

The actual [A2 Guidance of Charge Pad article](https://support.unitree.com/home/en/A2_SDK_Development_Guide/a2_charge_pad) describes a **457 × 330 × 19.5 mm flat pad**, external lithium-battery charger, **58.8 V / 7 A / 411.6 W**, a stated 1 h 50 min charge time, ideal 5–40 °C charging, ideal 22–28 °C storage, IP67, ≤95% relative humidity, 70–106 kPa and natural cooling. The BA2 product page instead specifies the values in the table above. Do not combine the pad's IP67, charging time, ideal storage or 7 A behavior into a dock specification.

That pad article gives green powered-idle/red charging indicators, a model handshake through bottom electrodes, >15 A abnormal-current detection, automatic short-circuit recovery, contact-jitter interruption/retry and <1 A full-charge disconnection. **These are pad-specific descriptions, not verified BA2 thresholds, LEDs or recovery rules.** The dock page's full-charge criterion is a voltage threshold. Its matching handshake/control implementation remains unverified. The original pad drawing visibly shows a separate brick and a thin floor plate, confirming that this is not merely an alternative rendering of the upright autonomous dock.

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

### Contacts, siting and electrical boundary <a href="#contacts-siting-and-electrical-boundary" id="contacts-siting-and-electrical-boundary"></a>

Unitree says the dock's metal contacts remain concealed and emerge during return-to-charge, reducing incidental contact and contamination. The page illustrates an independent power control and internal electrical protections. Neither illustration establishes connector pin assignments, protective-earth bonding, service isolation, polarity of accessible contacts, latch status signals or a charging-handshake circuit. Do not probe, bridge, force open or inject voltage into the contacts to identify them.

Use the delivered manufacturer-approved mains assembly and the exact compatible A2 charging interface. A site installation needs the actual dock operator/electrical documentation for anchoring, mains connection, earthing, isolation, service access and environmental sealing. No custom mains or output-harness recipe is supplied here because those facts are absent from the verified exact-product source. The IP56 claim does not authorize charging through pooled water or maintaining exposed connections outside their ratings.

![Unitree autonomous dock concealed-contact illustration](https://www.unitree.com/images/46a71c833672467b98c6eafec92364ab_1254x1260.png)

_Original Unitree dock image. It supports the concealed-contact design description, not a wiring or disassembly procedure._

### Positioning aids and storage <a href="#positioning-aids-and-storage" id="positioning-aids-and-storage"></a>

The exact product page offers optional reflective posts and QR-code markers for different positioning approaches, plus a base compartment for markers, posts and charging cables. Inventory actual supplied accessories separately from product-page possibilities. Do not assume marker dimensions, tag family/ID, coordinate axes, sensor extrinsics or a LiDAR reflector intensity threshold from an illustration. A reusable route must account for robot approach/posture clearance and the dock's fixed position; no exact exclusion-zone or anchoring drawing was verified.

### Excluded A2 expansion hub <a href="#excluded-a2-expansion-hub" id="excluded-a2-expansion-hub"></a>

The portal's `about_a2_nx` and `Installation_of_docking_modules` resources describe a **robot-mounted expansion compute hub** with mounting rails, computer power/network, GNSS/4G/serial and backup topics. They do not specify this autonomous charging dock. Their SSH addresses, companion-computer connectors, rail-fastener sizes and recovery images must not be applied to BA2. This distinction avoids interpreting the English word “docking” as electrical charging compatibility.

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### What is supported by the exact source <a href="#what-is-supported-by-the-exact-source" id="what-is-supported-by-the-exact-source"></a>

| Function                     | Verified statement                                            | Remaining integration contract                                                             |
| ---------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| Low-battery return           | Manufacturer says the A2 automatically returns on low battery | Threshold, trigger ownership, robot firmware/edition, retry policy, route/map dependencies |
| Position/posture/dock/charge | Product page describes the sequence                           | API/state identifiers, transition criteria, docking timeout and safe interruption          |
| LiDAR / QR positioning       | Optional aids supported conceptually                          | Sensor model, tag geometry/family, frames, detector output and calibration                 |
| Power control                | Independent control illustrated                               | Exact control action, isolation behavior and restart procedure                             |
| Charging protection          | Named electrical protection mechanisms                        | Fault codes, latching/reset behavior, conditions for automatic resumption                  |
| Full charge                  | Voltage-threshold termination                                 | Numeric threshold, status reporting, battery compatibility and hysteresis                  |

No BA2-specific public SDK repository, protocol packet definition, ROS/DDS topic, network address, diagnostic register map, firmware binary or sample charging client was established by the exact source. Do not implement a guessed `dock`, `charge`, battery-low API or reuse a Go2 recharge example. The appropriate dependency is a delivered A2/BA2 manufacturer integration package with matching hardware, battery, robot firmware and control software—not an arbitrary Unitree SDK installation.

The flat-pad portal article demonstrates that A2 charging can involve a model-recognition handshake, but does not publish the electrical encoding or prove that the autonomous dock uses the same implementation. Its simplified CAD archive is a **pad** resource and must not become the BA2 dock CAD link.

## Getting started <a href="#getting-started" id="getting-started"></a>

### First result: exact assembly and documentation check <a href="#first-result-exact-assembly-and-documentation-check" id="first-result-exact-assembly-and-documentation-check"></a>

The available evidence supports a useful identification checkpoint before any electrical commissioning:

1. Match the received dock, label, part/revision and approved accessory list against the manufacturer's **355 × 313 × 212 mm autonomous dock**, not the thin floor pad or robot expansion hub. Photograph its label and retain the exact operator/electrical documentation supplied with it.
2. Confirm written compatibility for the actual A2 hardware/firmware and battery part number, charging-contact assembly, input cable and site power arrangement. The common 58.8 V nominal output alone is insufficient.
3. Obtain the exact mounting/site-clearance, protective-earth/isolation, first-power and charging procedure, plus stop/fault recovery instructions and the system's charging-status contract. Identify who owns navigation, docking and battery decisions.
4. Record the planned return route, actual positioning accessories, measured dock/robot frame relationship and recovery policy. Leave unknown API names, tag IDs and thresholds explicitly unknown.

**Expected result:** a verified dock/robot/battery identity record and a complete model-matched commissioning package. It is not a successful charging test. If these records are missing, the current guide is a bounded engineering reference; first power, docking, charging and unattended operation are **not ready from these public sources alone**. This gate is specific to the unresolved BA2 installation/control evidence, not a request to run a generic SDK diagnostic.

### Conditional later commissioning <a href="#conditional-later-commissioning" id="conditional-later-commissioning"></a>

Only the manufacturer-approved integration procedure can specify initial energization, contact engagement, charge-state indication, safe interruption and recovery for the actual assembly. Keep the initial supervised check separate from automatic navigation and unattended deployment. Verify charging telemetry and controlled stop behavior through the documented interface before enabling low-battery return. No stand-up/lie-down command, movement sequence, handshake injector or firmware action is provided or executed here.

The flat-pad chapter's floor-sticker orientation, forward/backward lying posture, two exposed bottom electrodes, AC-then-pad connection sequence and no-side-lying warning are indexed below as **pad-only source coverage**. They must not serve as this dock's commissioning recipe.

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

| Observation                                      | Evidence-based next step                                                                                                                                                          |
| ------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Robot does not return on low battery             | Confirm the actual integration package enables the function, who owns the trigger, route/localization readiness and the delivered firmware/edition; no threshold/API was verified |
| Robot approaches but fails to dock               | Compare the actual dock pose, accessories and manufacturer positioning contract; 40 mm X/Y tolerance does not diagnose angular or posture error                                   |
| Contact engagement produces no charge            | Stop the sequence through the supplied approved procedure and check exact battery/robot compatibility and diagnostic status; don't bridge contacts or emulate a handshake         |
| Unexpected charge termination                    | Exact dock page says voltage-threshold cutoff; do not import the pad's <1 A threshold or assume all stops mean full battery                                                       |
| Protection trips / repeated restart              | Obtain actual fault meaning and recovery behavior; named overcurrent/temperature protections do not establish thresholds or automatic restart rules                               |
| Green/red indication differs from online article | Those colors are documented for the flat pad, not verified for BA2; use the exact dock manual                                                                                     |
| Outdoor installation questions                   | Dock IP56 and 0–40 °C operation are bounded ratings; separately verify power-cable/site protection, drainage and actual approved installation                                     |
| “Docking hub” instructions show SSH/GNSS         | Wrong accessory category: those resources describe a robot companion-computer hub                                                                                                 |

**May I use it on B2, As2 or Go2?** No compatibility was established in the examined exact dock source; it explicitly targets A2.

**Does IP56 mean all-weather unattended charging is already validated?** It is a dock ingress claim, not validation of the robot, installed electrical system, navigation availability or emergency behavior.

**Are there firmware/recovery commands?** None verified for this exact dock. A2 expansion-computer backup images and pad reset behaviors are different products. Obtain the delivered firmware identity, supported update tool, image validation and recovery procedure before an update. No battery replacement, pack opening, charger modification or flashing procedure is inferred.

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

| Resource                                                                                                                  | Role and scope                                                                                                                                             |
| ------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [A2 autonomous charging dock product/specification page](https://www.unitree.com/A2/ChargingDock/)                        | Exact hardware identity, dimensions, ratings, functions and original product illustrations; full page reviewed                                             |
| [Original positioning illustration](https://www.unitree.com/images/979c7ec41ec943abb2a6b2aea76a1817_1282x707.png)         | Optional positioning concept; not a calibrated installation drawing                                                                                        |
| [Original storage-compartment illustration](https://www.unitree.com/images/f65c1aa9654d447eafcf9071bed4ee9c_1282x474.png) | Storage/accessory concept; no verified bill of delivered accessories                                                                                       |
| [A2 contact charging-pad article](https://support.unitree.com/home/en/A2_SDK_Development_Guide/a2_charge_pad)             | Different flat-pad hardware; comparison and exclusion evidence only                                                                                        |
| [Exact dock operator manual / electrical schematic / CAD / SDK / firmware](https://www.unitree.com/A2/ChargingDock/)      | No exact downloadable package verified on the inspected product page; request model/revision-matched deliverables rather than substitute the pad's archive |

The final row links the exact product reference for identification; it does **not** claim those missing files can be downloaded there. No current OpenELAB SKU or store-page match is asserted.

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

Reviewed 24 November 2026 against the actual complete manufacturer dock page, all its functional/specification sections and selected original illustrations. Also read the complete actual A2 flat-pad article and the two A2 expansion-hub articles to prevent scope transfer. The official article asset contents were accessible and read; this does not mean an exact BA2 developer manual or every A2 portal chapter was found. Full section crosswalk and source hashes accompany this draft.

**No SDK installation/import/build, ROS/DDS, mains or contact measurement, robot motion, docking, charging, firmware or recovery test was performed.** The guide's verified first result is document/identity readiness only. Material gaps are exact retail SKU, dock operator/electrical/CAD documentation, battery/firmware compatibility, grounding and contact/handshake definitions, public control/diagnostic interface, stop/retry/fault behavior and update/recovery. These gaps are retained explicitly; the source's autonomous-operation claim is not presented as independently tested performance.

### Complete official article coverage <a href="#complete-official-article-coverage" id="complete-official-article-coverage"></a>

Each row records substantive functional coverage, not a claim that a link alone was reviewed. Full source heading/line ranges and hashes are retained with the draft. Empty category nodes are explicitly distinguished from technical content.

| Actual official article                                                                                                    | Source sections read                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | Original engineering coverage / boundary                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Guidance of Charge Pad](https://support.unitree.com/home/en/A2_SDK_Development_Guide/a2_charge_pad)                       | Basic Information; Functional Description; Usage Instructions                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | This flat457×330×19.5 mm pad with external charger is not the355×313×212 mm autonomous dock. Its58.8 V/7 A/411.6 W,IP67,1h50 charge,ideal environmental limits, green/red LEDs, model handshake,>15 A alert,<1 A cutoff and automatic short/jitter recovery are pad-only facts. Its inspection, AC-then-pad connection, forward/reverse floor-sticker lying posture and no-side-lying instructions are excluded from BA2 commissioning until explicit compatibility proof. |
| [Install guide for docking and modules](https://support.unitree.com/home/en/A2_SDK_Development_Guide/docking_installation) | Docking Station Installation Instructions; Assembling the Docking Station; Installing the Docking Station to the A2; Emergency Stop Button Installation Instructions; Companion Station Installation Instructions                                                                                                                                                                                                                                                                                                                                                                                                                                                      | A2 robot-mounted hub installation concerns rails/fasteners, antennas/GNSS, companion power/network and emergency-stop assembly. Those diagrams and interfaces do not establish the autonomous charging dock mounting, mains or battery-contact specification; the complete article was read to exclude this false match.                                                                                                                                                   |
| [Docking Hub User Manual](https://support.unitree.com/home/en/A2_SDK_Development_Guide/about_a2_nx)                        | 1. Connection Methods; 1.1 Display Connection; 1.2 Remote SSH Connection; 1.3 NoMachine Remote Desktop Connection; 2. Instructions for CAN and RS485 Interfaces; 3. Instructions for 4G Modem; 4. Instructions for GNSS Positioning Module; 4.1 Serial Port Configuration; 4.2 Directly Read GNSS Raw Data; 4.3 View GNSS Data via cgps; 5. Timeshift System Backup and Restore Instructions; 5.1 Package Installation; 5.2 First Launch and Wizard Configuration; 5.3 Create a System Snapshot; 5.4 System Restore (System is Bootable); 5.5 Factory‑Preloaded Restore Snapshot (Version 20260907 and later); 6. Notes on Upgrading Software Packages Such as JetPack | Robot expansion-compute hub covers companion network/serial/GNSS/4G and backup topics; it is not a charging dock. No SSH address, computer firmware image, serial device, connector voltage or restore procedure is transferred to BA2.                                                                                                                                                                                                                                    |

**Related documentation:** [Unitree model and development directory](./).
