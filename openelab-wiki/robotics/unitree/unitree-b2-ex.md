---
description: >-
  Distinguish B2-Ex chassis and inspection-solution specifications and
  advertised protection markings, with explicit certificate, power, stop and
  software evidence requirements.
---

# Unitree B2-Ex: chassis and inspection-solution engineering boundaries

{% hint style="info" %}
**Manufacturer model reference: Unitree B2-Ex.** No exact B2-Ex OpenELAB listing or SKU was verified. **SKU:** unverified · **Store URL:** unverified. This page distinguishes the chassis and inspection-solution configurations. It grants no hazardous-area deployment clearance. [Official Unitree B2-Ex page](https://www.unitree.com/B2-Ex/).
{% endhint %}

## Product overview <a href="#product-overview" id="product-overview"></a>

Unitree B2-Ex is a separately named industrial quadruped presented by the manufacturer for inspection applications requiring explosion-protection engineering. Its official table distinguishes **B2-Ex (Chassis)** from **B2-Ex Inspection Solution**, with different protection markings, dimensions, mass, payload interpretation and slope figures. It is not a synonym for ordinary [B2](unitree-b2.md), and no B2-W wheel/control/charging assumption is applied here. [Primary configuration table](https://www.unitree.com/B2-Ex/)

This is a manufacturer model reference with an explicit deployment evidence gap. The reviewed source is a living product page, not a certificate, certificate schedule, installation manual or site acceptance record. The first result is an offline configuration/evidence review. No SDK or physical connection is proposed until the actual configuration, certification conditions, power/stop design and firmware interface have been established.

## Applications <a href="#applications" id="applications"></a>

The manufacturer describes route-based inspections, equipment-status collection and assisted anomaly identification at industrial sites, including oil/gas and chemical facilities. Listed payload integration categories include PTZ/visible/thermal cameras, gas sensing/imaging, acoustic imaging, communications, LiDAR and robotic arms. These are integration capabilities and proposed applications, not proof that every attached sensor/arm is covered by a particular robot certificate.

For the inspection-solution column, the page lists front/rear explosion-proof LiDAR, a bi-spectrum PTZ, gas detection and autonomous navigation as standard/supported. The chassis column marks these superstructure items `/`. A chassis procurement therefore must not be described as including the complete navigation and inspection payload. Exact payload models, mounting, cables, software and certificate inclusion still require a delivered bill of materials. [Manufacturer integration and superstructure sections](https://www.unitree.com/B2-Ex/)

## Specifications <a href="#specifications" id="specifications"></a>

These are **advertised configuration values**, not independently tested ratings or certified installation conditions.

| Parameter                            | B2-Ex (Chassis)                                              | B2-Ex Inspection Solution                                                                       |
| ------------------------------------ | ------------------------------------------------------------ | ----------------------------------------------------------------------------------------------- |
| Printed explosion-protection marking | `Ex db mb IIB T4 Gb`                                         | `Ex db eb ib mb IIB T4 Gb`                                                                      |
| Standing dimensions, L × W × H       | 1085 × 685 × 710 mm                                          | 1320 × 685 × 965 mm                                                                             |
| Mass with battery                    | Approximately 130 kg                                         | Approximately 170 kg                                                                            |
| Joint motors                         | 12                                                           | 12                                                                                              |
| Battery                              | 60 Ah / 3072 Wh, lithium battery                             | 60 Ah / 3072 Wh, lithium battery                                                                |
| Charging method                      | Manual / wireless charging                                   | Manual / wireless charging                                                                      |
| Advertised endurance                 | ≥7 h; detailed duty/load conditions not supplied in this row | ≥4 h with 40 kg payload, approximately 80 W average external load power and stable conditions   |
| Payload wording                      | Continuous walking 40 kg; maximum 70 kg                      | “Standard Superstructure”; no separate additional payload allowance established by this wording |
| Slope / stairs                       | Standard 45°; stairs 20–25 cm                                | Standard 30°; stairs 20–25 cm                                                                   |
| Speed                                | 0–1 m/s, under safe conditions                               | 0–1 m/s, under safe conditions                                                                  |
| Operating temperature                | −20 to +55 °C                                                | −20 to +55 °C                                                                                   |
| External interface / accessories     | Ethernet; standard charger and remote                        | Ethernet; standard charger and remote                                                           |

Source: [B2-Ex Basic Parameters, Electrical Parameters, Superstructure and Accessories tables](https://www.unitree.com/B2-Ex/). The same page's core-parameter block advertises IP66; do not replace it with ordinary B2's IP67 or B1's IP68 headline.

The 60 Ah/3072 Wh line does not state a verified pack terminal voltage, charge-limit voltage, charger output or accessory power budget. No voltage is inferred by dividing energy by capacity. Likewise, maximum 70 kg and continuous 40 kg chassis payload are different conditions; the inspection solution's standard superstructure must not receive an assumed extra 70 kg payload.

### Protection-marking boundary <a href="#protection-marking-boundary" id="protection-marking-boundary"></a>

The two exact markings above are what the product table prints. Their presence does not identify a certificate number, issuing body, applicable standard edition, approved nameplate/model suffix, special conditions of use, permitted area classification or maintenance procedure. No certificate or schedule was supplied/read in this task. The page says core power systems/motors follow independent certification requirements, but component certification is not a reviewed certificate for the final assembled robot and payload.

Before any hazardous-area deployment, obtain the actual unit's certificate and schedule, full nameplate, delivered BOM and manufacturer installation/maintenance instructions. Check the site's relevant conditions against those documents, including permitted atmosphere, ambient range, battery/charging arrangement, enclosure/cable entries, added payloads and any special conditions. This is an unresolved document checklist, not a legal interpretation of the marking or an authorization to enter a particular zone. Even the product page's −20 to +55 °C entry must not be assumed to be the certificate's allowable ambient range. Ordinary B2 or B2-W references cannot close this gap.

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

### Configuration and power identification <a href="#configuration-and-power-identification" id="configuration-and-power-identification"></a>

Identify which table column matches the delivered nameplate and BOM. The two configurations differ by roughly 40 kg before additional handling details are known, and the inspection solution has a higher superstructure. Lifting points, rail/fastener loads, center-of-mass allowance, restraint and tip stability require the exact mechanical drawings; none is established by the exterior dimensions alone.

The product page lists Ethernet but supplies no mating connector orientation/pin assignment, allowed external power rails or host address configuration. Do not infer the ordinary B2 interface module or connect a generic Ethernet/PoE or external supply arrangement. Likewise, “manual/wireless charging” identifies offered methods, not an interchangeable B2 contact charger or an approved charging location. Confirm the exact battery, charger, wireless charging assembly and their instructions before power is applied. [B2-Ex configuration source](https://www.unitree.com/B2-Ex/)

### Stops, environmental protection and modification control <a href="#stops-environmental-protection-and-modification-control" id="stops-environmental-protection-and-modification-control"></a>

No B2-Ex-specific remote manual, low-level stop behavior, safe power-loss posture, e-stop circuit or recovery sequence was established in the read sources. Therefore B2's L2/button sequences and B2-W mode changes are not carried into this reference. An Ethernet disconnect is not a proven robot stop, and a software StopMove method from another model is not a verified independent safety function.

For an already installed machine, preserve its manufacturer-approved configuration and require the appropriate operator/engineering process to establish the stop, isolation and recovery plan. Do not open enclosures, change cable glands, swap batteries/chargers or add electrical payloads based on this page. The missing certificate/installation documents must first identify what configuration and servicing are permitted. No disassembly, hot-swap or power-on procedure is supplied here.

IP66 and an explosion-protection marking address different claims; neither establishes the other. No immersion depth/duration, cleaning chemistry, pressure-wash procedure or battery-compartment opening condition was verified. Inspect and maintain only under the exact manufacturer procedure once obtained, rather than inheriting ordinary B2's cleaning or pack-removal instructions.

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

| Resource                                                                                                  | What it establishes                                                | What it does not establish for B2-Ex                                                                          |
| --------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------- |
| Official B2-Ex page                                                                                       | Chassis/solution scope and advertised navigation/payload functions | SDK package, message IDL, API service version, firmware range, network defaults or developer access           |
| Reviewed SDK2 C++ commit `b7fec6020eb93d4c059a6edf19905e12a75a8d3d`                                       | B2 and B2-W source examples exist                                  | No B2-Ex-specific example/interface pairing was established from that evidence                                |
| SDK2 Python commit `814556d15970dd2ecf1c9984e845ca02ab07e206`                                             | GO message contracts and B2/B2-W example maps can be inspected     | Shared naming/body ancestry does not establish B2-Ex compatibility, active-joint map or permission to operate |
| Shared [SDK2 state guide](unitree-sdk2-state-development.md) / [ROS 2 guide](unitree-ros2-integration.md) | General source-review and isolation methods                        | Neither overrides the missing B2-Ex-specific commissioning contract                                           |

No SDK2, legacy UDP SDK or ROS package is declared compatible with B2-Ex hardware here. A twelve-motor count is insufficient to select GO versus another message contract, joint order or motor mode. Do not run a B2 stand example against B2-Ex: it releases a mode and publishes joint commands on assumptions not verified for this model. [Example audited as ordinary B2 only](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/b2/b2_stand_example.cpp)

The next software evidence needed is an exact manufacturer package/release with a B2-Ex support statement, controller/firmware pairing, environment requirements, IDL/topic or request schema, network configuration and an approved receive-only diagnostic. Until then, do not initialize DDS, discover a live industrial network, import a guessed decoder or substitute another model's firmware.

## Getting started <a href="#getting-started" id="getting-started"></a>

### Offline first result: reject incomplete deployment evidence <a href="#offline-first-result-reject-incomplete-deployment-evidence" id="offline-first-result-reject-incomplete-deployment-evidence"></a>

1. With the machine/network untouched, record chassis versus inspection solution from the actual nameplate/BOM. Do not choose by outward appearance or the general B2 name.
2. Collect the certificate plus schedule, approved installation/charging instructions, stop/isolation document, connector/power definition and firmware/interface pairing. Mark absent evidence as missing rather than treating the product page as its substitute.
3. Run this original standard-library Python worksheet locally. All inputs below are deliberately incomplete to reflect this source-only review.

```python
REQUIRED = ("nameplate_match", "certificate_and_schedule", "installation_conditions",
            "approved_power_and_charger", "independent_stop_plan", "firmware_interface")

def inspect_b2ex_evidence(config, records):
    if config not in ("chassis", "inspection-solution"):
        raise ValueError("Choose the actual B2-Ex configuration")
    missing = [name for name in REQUIRED if records.get(name) is not True]
    return {"model": "B2-Ex", "configuration": config,
            "missing": missing, "next_action": "document review" if missing else "qualified review",
            "hardware_tested": False, "deployment_authorized": False}

print(inspect_b2ex_evidence("chassis", {"nameplate_match": False}))
```

**Expected result:** all six evidence categories remain missing, `hardware_tested` is false and `deployment_authorized` is false. The function must reject an unknown configuration. Even setting every flag true produces only “qualified review”; this original worksheet never grants deployment authorization. It does not validate a certificate or contact hardware.

Once the documents have been substantively reviewed and per-unit conditions resolved, a separate authorized commissioning procedure can choose a passive first observation. No live topic/API command is specified here because the model's transport, firmware and stop conditions remain unverified.

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

**Does “B2-Ex” mean an ordinary B2 is explosion protected?** No. This page covers a distinct manufacturer model with separate chassis/solution markings and substantially different mass/configuration. A label in another product's name cannot be transferred to B2 or B2-W.

**May I treat the printed marking as site clearance?** No certificate or schedule was reviewed. Preserve the exact printed string, then obtain the actual certificate and operating conditions for the delivered BOM. The page does not certify the site's atmosphere, installation or added payload.

**Which battery or charger is interchangeable?** None was established. The page gives energy/capacity and manual/wireless charging categories, not matched part numbers or DC ratings. Do not copy B2's electrical values or contact-pad alignment instructions.

**Can the inspection solution carry the chassis's maximum payload in addition to its sensors?** The table's solution payload cell says Standard Superstructure. Additional payload allowance, stability and certification scope require configuration-specific evidence.

**Can I use the B2 GO decoder because both robots have twelve motors?** Motor count is insufficient. No B2-Ex IDL/API or firmware pairing was verified. Obtain its own receive-only diagnostic rather than probing with a command-producing B2 example.

**Where are firmware, calibration and recovery instructions?** They were not established by the read product page. There is no guessed reset, downgrade, recalibration or service-mode procedure in this guide.

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

| Resource                                                                                                                               | Actual access and use                                                                                                                                               |
| -------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Official B2-Ex model page](https://www.unitree.com/B2-Ex/)                                                                            | Read model-specific introduction, integration text and full chassis/solution parameter table. Primary source for the advertised markings and conditional endurance. |
| [Original manufacturer B2-Ex page illustration resource](https://www.unitree.com/images/96038d39c91a4e64999f07a4864d7a05_1006x782.png) | Image URL observed in the product HTML; image contents not used as a certificate, dimensioned drawing or wiring source.                                             |
| Certificate and schedule, including any special conditions                                                                             | Not supplied/read. Obtain for the exact nameplate and assembled configuration; no certificate number is invented.                                                   |
| Installation, stop/isolation, battery/charger, remote and maintenance manuals                                                          | No exact B2-Ex edition was established in the private manual set reviewed here. B2/B2-W documents remain separate.                                                  |
| SDK/firmware/IDL and mechanical/electrical drawings                                                                                    | Exact B2-Ex releases and drawings unresolved. General SDK indexes are discovery aids only.                                                                          |

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

Reviewed 24 November 2026 from the cached official B2-Ex product HTML and range/source inventory, with relevant B2/B2-W SDK examples inspected only to bound unsupported transfer. The product page is undated and living; its cached content hash is retained privately. No complete B2-Ex user manual, certificate, portal chapter set or firmware release was read.

**Validation:** original offline worksheet plus missing/unknown-configuration cases, source hashes and nine-section structure checked. **Not run:** SDK imports, dependency installation/build, ROS/DDS/network discovery, hardware, motion, charging or flashing. Hardware/deployment readiness remains a draft because certification conditions, power/stop procedures and the software interface are unresolved. The ordinary browser's parent-owned portal access does not imply these B2-Ex resources have been read.

**Related documentation:** [Unitree model and development directory](./).
